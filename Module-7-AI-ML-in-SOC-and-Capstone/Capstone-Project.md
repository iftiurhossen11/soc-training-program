# Advanced Capstone Project: Automated Threat Detection & Response (Mini SOC)

## 🎯 Project Objective

The objective of this capstone project is to design, implement, and document a Mini Security Operations Center (Mini-SOC) environment that detects SSH brute-force activity using Splunk and automates the response by blocking a suspected source IP address.

The project combines Security Information and Event Management (SIEM), threat detection, Python automation, and firewall enforcement to simulate a Security Orchestration, Automation, and Response (SOAR) workflow.

**Core workflow:**

1. Generate authorized SSH authentication failures in an isolated lab.
2. Collect and forward authentication logs to Splunk.
3. Detect repeated failed login attempts using a Splunk search and alert.
4. Extract the suspected source IP address from matching events.
5. Validate the detection and apply a firewall block through a Python response script.
6. Verify the response and document the incident.

> **Safety note:** Run attack simulations only against systems you own or are explicitly authorized to test. Keep the lab isolated from production networks and the public internet. Use a dedicated test account rather than attempting to compromise real accounts.

---

## 🛠️ Tools & Environment Used

| Component | Tool / Technology | Purpose |
|---|---|---|
| Attacker Machine | Kali Linux | Authorized attack simulation and network reconnaissance |
| Target Machine | Ubuntu Server VM | SSH authentication log generation |
| SIEM Platform | Splunk Enterprise | Log ingestion, searching, alerting, and investigation |
| Automation | Python 3 | Alert processing and automated response |
| Python Libraries | `requests`, optional Splunk SDK | API communication and alert retrieval |
| Firewall | `iptables` or `ufw` | Blocking a confirmed test source IP |
| Log Source | `/var/log/auth.log` or the configured SSH authentication log | Recording authentication activity |
| Virtual Network | Host-Only Network | Isolating the lab environment |
| Example Network | `192.168.56.0/24` | Private lab subnet |

**Example lab addresses**

- Kali Linux (Attacker): `192.168.56.20`
- Ubuntu Target: `192.168.56.10`
- Splunk Server: Use the IP address configured for your lab.

These addresses are examples. Replace them with the actual IP addresses assigned to your virtual machines.

---

## 🏗️ Project Architecture

```text
+-----------------------+
| Kali Linux            |
| Authorized Test       |
| SSH Login Attempts    |
+-----------+-----------+
            |
            | SSH / TCP 22
            v
+-----------------------+
| Ubuntu Target         |
| SSH Authentication   |
| Logs                  |
+-----------+-----------+
            |
            | Log Forwarding
            v
+-----------------------+
| Splunk Enterprise     |
| Search & Detection    |
| Alert Generation      |
+-----------+-----------+
            |
            | Alert / API
            v
+-----------------------+
| Python Automation     |
| Alert Validation      |
| Source IP Extraction  |
+-----------+-----------+
            |
            | Authorized Response
            v
+-----------------------+
| Target Firewall       |
| Block Test Source IP  |
+-----------------------+
```

**Important design consideration:** A Splunk alert does not automatically execute a Python script merely because a webhook action is selected. A webhook receiver or other supported integration must receive the alert and securely invoke the response workflow. Alternatively, a Python process can poll the Splunk API for saved-search results or triggered-alert data.

---

# 📝 Project Phases

## Phase 1: Environment Preparation

### Step 1.1 — Verify the Lab Setup

Start the following virtual machines:

- Kali Linux (Attacker)
- Ubuntu Server (Target)
- Splunk Enterprise Server

Confirm that the machines are connected to the same isolated Host-Only network.

On Kali Linux, inspect the network configuration:

```bash
ip addr
ip route
```

On Ubuntu, inspect its network configuration:

```bash
ip addr
ip route
```

Confirm that each VM has an address in the expected lab subnet.

### Step 1.2 — Test Network Connectivity

From Kali Linux, test connectivity to the Ubuntu Target:

```bash
ping -c 4 192.168.56.10
```

If the target does not respond, check the VM network settings, routing, and firewall configuration. A failed ping does not necessarily mean the target is unreachable because ICMP traffic may be blocked.

### Step 1.3 — Enable SSH on the Target

On Ubuntu Server:

```bash
sudo systemctl enable --now ssh
```

Check the service status:

```bash
sudo systemctl status ssh
```

Verify that SSH is listening:

```bash
sudo ss -tlnp | grep ':22'
```

If SSH is not installed, install the OpenSSH server package before enabling the service:

```bash
sudo apt update
sudo apt install openssh-server -y
```

### Step 1.4 — Configure Log Ingestion in Splunk

Ensure that Splunk receives SSH authentication events from the Ubuntu Target.

Depending on the Ubuntu release and logging configuration, authentication events may be available in:

```text
/var/log/auth.log
```

Some systems primarily use the systemd journal instead. Verify the actual log source on your target.

Check the log locally:

```bash
sudo tail -n 20 /var/log/auth.log
```

If the file exists, follow new entries during testing:

```bash
sudo tail -f /var/log/auth.log
```

Configure the appropriate Splunk Universal Forwarder or other approved log collection method to forward the authentication log. Confirm that the target data is assigned to the intended index and sourcetype.

Example values:

```text
Index: main
Sourcetype: linux_secure
```

These are example settings; use the actual values configured in your Splunk environment.

### Step 1.5 — Verify Events in Splunk

Open Splunk Search & Reporting and run:

```spl
index=main sourcetype=linux_secure
```

Search for failed SSH authentication events:

```spl
index=main sourcetype=linux_secure "Failed password"
```

Confirm that the events contain the source IP address and username information needed for investigation.

**Expected result:** Authentication events appear in Splunk with usable timestamps and source details.

---

## Phase 2: Attack Simulation (Red Team)

This phase generates controlled authentication failures against the isolated Ubuntu Target to test the detection pipeline.

### Step 2.1 — Perform Network Reconnaissance

From Kali Linux, scan the authorized target:

```bash
nmap -sV -p 22 192.168.56.10
```

This checks the SSH port and attempts to identify the service version.

**Expected result:** If SSH is reachable, the output should show port 22 as open and may identify the SSH service.

### Step 2.2 — Generate Controlled SSH Authentication Failures

Use a dedicated, non-privileged test account created specifically for the lab. Do not use a real user's credentials or a production password list.

For a controlled test, perform a small number of manual SSH login attempts using an intentionally incorrect password:

```bash
ssh soc-test@192.168.56.10
```

Replace `soc-test` with the dedicated lab account. Enter an incorrect test password for a few attempts, then stop.

Alternatively, use a purpose-built test harness or an authorized lab-only password-testing tool with a small, controlled test list and strict attempt limits.

**Avoid running an unrestricted password list against an account.** The purpose of this phase is to generate enough authentication-failure events to validate detection, not to recover a password.

### Step 2.3 — Verify Generated Events

On the Ubuntu Target, inspect recent authentication messages:

```bash
sudo tail -n 50 /var/log/auth.log
```

In Splunk, search:

```spl
index=main sourcetype=linux_secure "Failed password"
```

Confirm that the failed attempts appear and that the `src_ip` field, or the equivalent extracted source-address field, is available.

**Expected result:** The controlled test attempts generate authentication failures that can be searched in Splunk.

---

## Phase 3: Detection Engineering (Blue Team)

### Step 3.1 — Create a Brute-Force Detection Search

Start with this search:

```spl
index=main sourcetype=linux_secure "Failed password"
| rex field=_raw "Failed password for (?:invalid user )?(?<user_name>\S+) from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| stats count as failed_attempts values(user_name) as usernames values(host) as target_hosts min(_time) as first_seen max(_time) as last_seen by src_ip
| where failed_attempts > 5
| convert ctime(first_seen) ctime(last_seen)
| sort - failed_attempts
```

This search:

1. Finds failed-password events in the selected index and sourcetype.
2. Extracts a username and IPv4 source address from matching log text.
3. Groups events by source IP.
4. Counts failed attempts and records the observed usernames and hosts.
5. Returns sources with more than five matching events.

**Important:** The regular expression is designed for common Linux OpenSSH authentication messages. Validate it against your actual logs. If Splunk already extracts `src_ip`, use the existing field instead of re-extracting it.

### Step 3.2 — Configure the Splunk Alert

In Splunk Search & Reporting:

1. Run the detection search.
2. Confirm that it returns the expected test source IP.
3. Save the search as an alert.
4. Configure the alert to run on a suitable schedule or trigger condition.
5. Set the trigger condition to detect more than five failed attempts in a one-minute window.
6. Enable the available alert history or notification action required by your workflow.

For a real rolling one-minute detection window, ensure that the saved search's time range and schedule cover that window. A search that counts all events in a larger time range may trigger incorrectly or late.

### Step 3.3 — Verify the Detection

Run the search again while generating controlled test events.

Check:

- Whether the source IP is identified correctly.
- Whether the failed-attempt count exceeds the configured threshold.
- Whether the alert triggers at the expected time.
- Whether the alert results contain the fields required by the response script.

**Expected result:** Splunk identifies a source generating repeated SSH authentication failures and triggers the configured alert.

---

## Phase 4: Automated Response (SOAR)

### Step 4.1 — Define the Response Workflow

The automated response should follow this sequence:

1. Receive an alert or retrieve eligible alert results from Splunk.
2. Extract the source IP from the alert data.
3. Validate that the IP is a valid IPv4 address.
4. Confirm that the IP belongs to the authorized lab subnet.
5. Ignore the target's own address, loopback addresses, and any explicitly approved management addresses.
6. Apply a temporary firewall block on the intended enforcement host.
7. Record the action, timestamp, and result.
8. Verify the firewall rule and test connectivity safely.

**Enforcement location matters:** To block an attacker from connecting to the target, the firewall rule must be applied on the target or on a network device that forwards the target's traffic. Running `iptables` on the Splunk server will not automatically block traffic to the Ubuntu Target.

### Step 4.2 — Understand the Firewall Rule

A rule such as the following drops inbound packets from a specified IPv4 source:

```bash
sudo iptables -I INPUT 1 -s 192.168.56.20 -j DROP
```

Replace `192.168.56.20` with the validated source IP from the test alert.

The command above is an example of the enforcement action, not a complete production-ready response system. Use it only on the designated lab target and only after validating the source address.

Verify the rule:

```bash
sudo iptables -L INPUT -n --line-numbers
```

**Caution:** An `INPUT` rule can affect more than SSH if the source is not otherwise restricted. In a real deployment, use a carefully scoped rule, a time-limited block, an explicit allowlist for management access, and a tested rollback procedure.

### Step 4.3 — Python Response Script Design

Create a file named:

```text
auto_block.py
```

The script should securely obtain alert results from the Splunk API, validate the source IP, and request a controlled firewall action on the target.

A safe implementation should include:

- Splunk API authentication using a protected token or secret store.
- TLS certificate verification.
- A strict allowlist of target hosts and lab IP ranges.
- Input validation with Python's `ipaddress` module.
- Deduplication to avoid repeatedly adding the same firewall rule.
- Logging of detection and response outcomes.
- A temporary block duration or a documented manual unblock procedure.
- A dry-run mode for testing without changing firewall state.

Do not place API tokens, passwords, or other secrets directly in a public repository.

### Step 4.4 — Example IP Validation Logic

The following snippet demonstrates the validation stage. It does **not** retrieve Splunk alerts or apply a firewall rule on its own.

```python
import ipaddress

LAB_NETWORK = ipaddress.ip_network("192.168.56.0/24")
TARGET_IP = ipaddress.ip_address("192.168.56.10")


def validate_source_ip(value: str) -> str:
    source_ip = ipaddress.ip_address(value)

    if source_ip.version != 4:
        raise ValueError("Only IPv4 addresses are allowed in this lab.")

    if source_ip not in LAB_NETWORK:
        raise ValueError("Source IP is outside the authorized lab subnet.")

    if source_ip == TARGET_IP:
        raise ValueError("The target IP cannot be blocked as an attacker.")

    if source_ip.is_loopback or source_ip.is_multicast:
        raise ValueError("This address is not valid for this response.")

    return str(source_ip)


if __name__ == "__main__":
    test_ip = "192.168.56.20"

    try:
        validated_ip = validate_source_ip(test_ip)
        print(f"Validated lab source IP: {validated_ip}")
    except ValueError as error:
        print(f"Validation rejected: {error}")
```

Before integrating this snippet with Splunk, make sure the alert's source IP is mapped correctly and that the enforcement action runs on the intended target. A production-ready script needs additional safeguards and error handling.

### Step 4.5 — Connect Splunk to the Response Workflow

Choose one supported integration design:

**Option A — Splunk API polling**

- Run a Python service that authenticates to Splunk.
- Query a saved search or eligible alert results.
- Process only new, qualifying results.
- Validate the source IP before requesting a firewall change.
- Store processed alert identifiers to prevent duplicate actions.

**Option B — Webhook receiver**

- Configure the Splunk alert to send a webhook to a controlled receiver.
- Authenticate the incoming request and validate its payload.
- Validate the source IP and alert context.
- Submit the response request to a restricted enforcement component on the target.

Do not expose an unauthenticated webhook that can execute arbitrary shell commands. The receiver should accept only the expected alert format and should never accept a raw command from the webhook payload.

### Step 4.6 — Verify the Automated Response

After the controlled test alert is processed:

1. Confirm that the response component received the alert.
2. Confirm that the source IP passed validation.
3. Check the Python response log for the action result.
4. Inspect the firewall rules on the target:

```bash
sudo iptables -L INPUT -n --line-numbers
```

5. Verify the intended traffic is blocked using an approved test method.
6. Confirm that authorized management access remains available.

A ping failure alone is not sufficient evidence that the firewall block worked, because ICMP may be blocked independently. Verify the specific traffic being controlled, such as SSH, and inspect the rule counters or system logs where available.

---

## Phase 5: Documentation and Incident Response

### Step 5.1 — Prepare the Incident Report

The final incident report should contain the following sections.

#### Executive Summary

Describe the controlled SSH brute-force simulation, the detection generated by Splunk, and the response action taken by the automation component.

Do not claim that a real attacker was stopped unless the evidence establishes that the activity was an actual attack rather than a lab-generated simulation.

#### Incident Timeline

| Event | Timestamp | Evidence |
|---|---|---|
| Lab test started | Record actual time | Test notes or terminal screenshot |
| SSH failures generated | Record actual time | Target authentication logs |
| Splunk detection search matched | Record actual time | Splunk search results |
| Splunk alert triggered | Record actual time | Alert history |
| Python response processed alert | Record actual time | Automation logs |
| Firewall block verified | Record actual time | Firewall rule output and test result |
| Block removed or expired | Record actual time | Firewall verification |

Use timestamps from your actual test. Do not invent event times.

#### Root Cause / Contributing Factors

For a lab simulation, document the test conditions that allowed the event to be generated and detected.

For a real incident, investigate whether the activity was caused by weak credentials, an exposed SSH service, password-based authentication, missing rate limits, or other contributing factors. Do not label weak credentials as the root cause without evidence.

#### Response and Remediation

Recommended defensive measures include:

- Disable direct root SSH login where operationally appropriate.
- Prefer SSH key-based authentication and protect private keys.
- Restrict SSH access to trusted networks or a VPN.
- Use a tool such as Fail2ban or an equivalent rate-limiting control.
- Review authentication logs and monitor repeated failures.
- Use least-privilege service accounts and firewall rules.
- Test alert thresholds to reduce false positives.
- Implement temporary blocks, audit logging, and a rollback process.
- Protect Splunk API credentials and restrict API permissions.
- Test the automation in dry-run mode before enabling enforcement.

### Step 5.2 — Collect Screenshot Evidence

Save the following evidence in the project's documentation directory.

| No. | Evidence | What It Should Demonstrate |
|---|---|---|
| 1 | Nmap Scan Output | SSH service discovery on the authorized target |
| 2 | Authentication Test Output | Controlled failed login attempts |
| 3 | Splunk Detection Results | Source IP and failed-attempt count |
| 4 | Splunk Alert History | The configured alert was triggered |
| 5 | Python Response Log | The alert was validated and processed |
| 6 | Firewall Rule Verification | The intended source IP rule exists |
| 7 | Response Validation | The expected traffic is blocked and management access remains available |

Use real screenshots captured from your own lab. Redact API tokens, passwords, session identifiers, and other sensitive information before publishing them.

Suggested directory structure:

```text
Mini-SOC-Capstone/
├── README.md
├── auto_block.py
├── requirements.txt
├── incident-report.md
├── screenshots/
│   ├── nmap-scan.png
│   ├── authentication-test.png
│   ├── splunk-detection.png
│   ├── splunk-alert.png
│   ├── python-response.png
│   └── firewall-verification.png
└── logs/
    └── sample-response.log
```

Only include files that actually exist in your repository. Do not commit credentials or sensitive production logs.

---

## 🧪 Validation Checklist

- [ ] Kali, Ubuntu Target, and Splunk are running on the isolated lab network.
- [ ] SSH authentication logs are being collected by Splunk.
- [ ] A controlled test generates failed SSH login events.
- [ ] The Splunk search identifies the correct source IP.
- [ ] The alert triggers at the configured threshold and time window.
- [ ] The response workflow authenticates securely to Splunk or receives a validated webhook.
- [ ] The source IP is validated before any firewall change.
- [ ] The firewall action is applied on the intended enforcement host.
- [ ] The response is verified using firewall output and a traffic test.
- [ ] The block can be safely removed or expires according to the design.
- [ ] Screenshots and the incident report document the actual results.
- [ ] No passwords, API tokens, or other secrets are committed to GitHub.

## 🎓 Key Skills Demonstrated

- SIEM deployment and Linux log ingestion
- Splunk Search Processing Language (SPL)
- SSH authentication monitoring
- Brute-force detection engineering
- Alert configuration and validation
- Python API integration
- Input validation and response automation
- Linux firewall management
- Incident documentation and evidence collection
- SOAR workflow design and testing

## ✅ Conclusion

This capstone project demonstrates how SIEM monitoring, detection engineering, and Python automation can be combined to build a Mini-SOC workflow. The lab simulates repeated SSH authentication failures, identifies suspicious activity through Splunk, and validates a controlled firewall response.

The project also highlights an important operational principle: automated containment must be carefully scoped, authenticated, logged, and reversible. A successful demonstration should prove not only that an alert fired and a firewall rule was created, but also that the correct source was identified, the intended traffic was blocked, and legitimate administrative access remained available.
