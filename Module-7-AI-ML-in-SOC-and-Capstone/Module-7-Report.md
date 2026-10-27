# Module 7: AI/ML in SOC & Capstone Project — Comprehensive Lab Report

## 📋 Module Overview

This final module explores the integration of Artificial Intelligence (AI), Machine Learning (ML), automation, and Security Orchestration, Automation, and Response (SOAR) into Security Operations Center (SOC) workflows.

The primary objectives are to understand how automation can reduce repetitive analyst tasks, use Python to enrich Indicators of Compromise (IoCs) through the VirusTotal API, and design a Mini-SOC workflow that detects suspicious SSH authentication activity and supports automated response.

The capstone project brings together skills developed throughout the SOC training program, including log analysis, SIEM detection, threat intelligence, incident investigation, and response automation.

## 🎯 Module Objectives

1. **Automation Fundamentals:** Understand how Python and APIs can automate repetitive SOC tasks.
2. **API Integration:** Develop a Python script that queries the VirusTotal API for IP reputation information.
3. **SOAR Concepts:** Understand how automated workflows can support actions such as creating incident tickets and blocking suspicious IP addresses.
4. **Capstone Project Design:** Design and document a Mini-SOC workflow for detecting SSH brute-force activity and initiating a response.
5. **Safe Response Automation:** Understand the importance of validation, permissions, and safeguards before applying firewall changes.

---

## 🛠️ Tools & Technologies Used

| Category | Tool / Technology |
|---|---|
| Programming Language | Python 3 |
| Python Library | `requests` |
| Threat Intelligence API | VirusTotal API v3 |
| SIEM Platform | Splunk Enterprise |
| Firewall Management | `iptables` |
| Operating System | Kali Linux VM |
| Attack Simulation | Hydra, in an isolated authorized lab |
| Automation Concepts | Python scripting, API integration, SOAR |

---

## 🔬 Lab 1: Python Automation for SOC — VirusTotal API Enrichment

### 1.1 Objective

To automate IoC enrichment using Python and the VirusTotal API. This lab demonstrates how a SOC analyst can retrieve IP reputation information programmatically instead of manually searching a threat intelligence website.

### 1.2 Detailed Execution Steps

#### Step 1: Obtain a VirusTotal API key

1. Create or sign in to a VirusTotal account.
2. Locate the account's API key.
3. Store the key securely as an environment variable.
4. Avoid placing the key directly in source code or committing it to a public GitHub repository.

For a Linux shell, set the key for the current terminal session:

```bash
export VT_API_KEY="YOUR_VIRUSTOTAL_API_KEY"
```

Replace the placeholder with your own key. Do not share the real key in screenshots, source code, or public repositories.

#### Step 2: Install the required Python library

```bash
python3 -m pip install requests
```

If the operating system manages Python packages externally, use a virtual environment rather than forcing a system-wide installation.

#### Step 3: Create the Python script

Create a file named `vt_automation.py` and add the following implementation:

```python
import os
import sys
import requests

API_URL = "https://www.virustotal.com/api/v3/ip_addresses/{}"


def enrich_ip(ip_address):
    api_key = os.getenv("VT_API_KEY")

    if not api_key:
        print("Error: VT_API_KEY environment variable is not set.")
        return

    headers = {"x-apikey": api_key}

    try:
        response = requests.get(
            API_URL.format(ip_address),
            headers=headers,
            timeout=20
        )

        if response.status_code == 401:
            print("Error: API key is invalid or unauthorized.")
            return

        if response.status_code == 429:
            print("Error: API rate limit reached.")
            return

        response.raise_for_status()
        data = response.json()["data"]["attributes"]

        stats = data.get("last_analysis_stats", {})

        print(f"IP Address: {ip_address}")
        print(f"Malicious: {stats.get('malicious', 'N/A')}")
        print(f"Suspicious: {stats.get('suspicious', 'N/A')}")
        print(f"Harmless: {stats.get('harmless', 'N/A')}")
        print(f"Undetected: {stats.get('undetected', 'N/A')}")

    except requests.exceptions.Timeout:
        print("Error: The request timed out.")
    except requests.exceptions.RequestException as error:
        print(f"Request error: {error}")
    except (KeyError, ValueError):
        print("Error: Unexpected or invalid API response.")


if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("Usage: python3 vt_automation.py <IP_ADDRESS>")
        sys.exit(1)

    enrich_ip(sys.argv[1])
```

**How it works:**

- `os.getenv()` reads the API key from an environment variable.
- `requests.get()` sends a request to the VirusTotal API v3 IP address endpoint.
- The `x-apikey` header authenticates the request.
- `response.json()` parses the returned JSON.
- `last_analysis_stats` contains available analysis counts.
- Exception handling helps the script report common API and network failures.

The script demonstrates API integration for IP addresses. A production implementation should also validate IP address input, handle unexpected response structures comprehensively, and account for API quotas.

#### Step 4: Execute the script

```bash
python3 vt_automation.py 8.8.8.8
```

The script will query VirusTotal and display the analysis statistics returned by the API.

#### Step 5: Verify the output

The original lab notes recorded the following output for `8.8.8.8`:

```text
IP Address: 8.8.8.8
Malicious: 0
Suspicious: 0
Harmless: 53
```

These values are the recorded example from the lab notes, not guaranteed current results. The actual output depends on the API response at execution time. The script may also display an `Undetected` count.

### 1.3 Expected Outcome & Verification

- **Expected outcome:** A Python script that requests IP reputation information from VirusTotal.
- **Verification:** Execute the script with an IP address and confirm that it successfully parses and displays the API response.
- **Security verification:** Confirm that the API key is loaded from the environment and is not exposed in the repository.

### 1.4 Key Learnings & Troubleshooting

- **API security:** Never hardcode an API key in a public repository.
- **Authentication:** A `401` response may indicate an invalid or unauthorized API key.
- **Rate limiting:** A `429` response indicates that the request limit has been reached.
- **Network connectivity:** Check internet access, DNS resolution, and connectivity if the request fails.
- **Reputation interpretation:** Zero malicious detections do not prove that an IP address is completely safe.
- **Data freshness:** API results can change; record the lookup date when documenting an investigation.

---

## 🏆 Advanced Capstone Project: Automated Threat Detection & Response

### 2.1 Project Objective

To design and document a Mini-SOC environment that identifies repeated SSH authentication failures using Splunk and supports automated containment through Python and `iptables`.

The workflow combines SIEM-based detection, attacker IP extraction, validation, and a controlled firewall response.

**Project scope:** The workflow should be tested only in an isolated, authorized lab environment. Automatic blocking must not be enabled against production systems without appropriate approval, testing, logging, and rollback procedures.

### 2.2 Project Phases

#### Phase 1: Environment Preparation

Prepare the lab components:

- Kali Linux VM for administration and monitoring.
- A separate target VM with SSH enabled.
- Splunk Enterprise for log ingestion, search, and alerting.
- An isolated virtual network connecting the lab systems.
- Python and the necessary permissions for the response component.

Verify that the target's SSH authentication logs are being collected and that Splunk can search them before proceeding.

#### Phase 2: Authorized Attack Simulation

The original project used Hydra to simulate repeated SSH authentication failures against the target VM.

Perform attack simulation only against a system you own or have explicit permission to test. Use a controlled test account and a lab-only network.

Confirm that the test attempts appear in the target's authentication logs before building the detection rule.

#### Phase 3: Detection Engineering in Splunk

The initial project notes describe a Splunk alert using:

```spl
search count > 5
```

This expression alone is not a complete brute-force detection query. A meaningful detection should count failed authentication events over a defined period and, where possible, group the events by source IP and target account.

For example, if your events are indexed in Splunk with the `linux_secure` sourcetype and include the text `Failed password`, a basic query is:

```spl
index=* sourcetype=linux_secure "Failed password"
| rex field=_raw "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| stats count AS failed_attempts by src_ip
| where failed_attempts > 5
```

**Important:** Replace `index=*` with the correct index after verifying your log source. This example extracts IPv4-shaped text; it does not fully validate IP addresses. It also counts matching events across the selected search time range, so the alert schedule and time window must be configured deliberately.

For a production-quality detection, consider grouping by both source IP and target account, using a defined time window, and validating that the extracted address represents the remote client.

#### Phase 4: Automated Response Design

The proposed response component follows this sequence:

1. Receive or retrieve a qualifying Splunk alert.
2. Extract the source IP associated with the alert.
3. Validate the IP and confirm that it meets the containment policy.
4. Check whether the IP is already blocked or belongs to an approved exception list.
5. Apply the firewall rule only after validation and authorization.
6. Record the decision, timestamp, triggering event, and action result.
7. Provide a rollback procedure to remove an incorrect block.

The original project description specifies a Python script that polls the Splunk API and uses `iptables` to block an identified source IP. This report documents the architecture; it does not establish that a live, end-to-end automated block was successfully executed.

#### Phase 5: Incident Response Documentation

Document the test scenario and results in `Capstone-Project.md`, including:

- Lab topology and system roles.
- Log source and Splunk detection logic.
- Alert threshold and search time range.
- Evidence from the controlled test.
- Source IP validation and containment decision.
- Firewall action result, if actually tested.
- Rollback and recovery procedure.
- Limitations and proposed improvements.

### 2.3 Expected Outcome & Verification

- **Expected outcome:** A documented Mini-SOC workflow connecting authentication logs, Splunk detection, Python orchestration, and firewall response.
- **Detection verification:** Confirm that controlled test events are searchable and that the detection identifies the expected source.
- **Response verification:** If automated blocking was implemented, verify the firewall rule and test the rollback procedure.
- **Documentation verification:** Ensure that screenshots and reports distinguish between a designed workflow, a simulated event, and a successfully tested response.

### 2.4 Key Learnings & Troubleshooting

- **SOAR workflow:** Automation can reduce repetitive analyst work and support faster incident handling.
- **Alert quality:** Detection thresholds must be tied to a clear event type, grouping strategy, and time window.
- **Least privilege:** Grant the response component only the permissions it needs.
- **Safe containment:** Validate addresses and maintain an allowlist for trusted infrastructure before blocking.
- **Auditability:** Record every automated decision and its outcome.
- **Recovery:** A containment workflow should include a tested method to remove an incorrect block.
- **Troubleshooting:** Confirm Splunk API access, correct index and sourcetype, source IP extraction, firewall permissions, and network isolation.

---

## 🏛️ SOAR Workflow Architecture

The following diagram represents the intended capstone architecture.

```mermaid
flowchart LR
    A["Controlled SSH Test<br/>(Hydra in Lab)"] --> B["Target Authentication Logs"]
    B --> C["Splunk Detection<br/>(Failed Login Threshold)"]
    C --> D["Python Response Worker<br/>(Alert/API Processing)"]
    D --> E["Validate Source IP<br/>(Policy and Exceptions)"]
    E --> F["Firewall Action<br/>(iptables)"]
    F --> G["Audit Log and Verification"]
    G --> H["Rollback if Required"]

    classDef step fill:#1f3a5f,color:#fff,stroke:#0e1f33,stroke-width:2px
    class A,B,C,D,E,F,G,H step
```

### Workflow Explanation

1. **Controlled test:** Generate authorized SSH authentication failures in the isolated lab.
2. **Log collection:** Ensure the target system's authentication events reach Splunk.
3. **Detection:** Identify repeated failures that meet the configured threshold.
4. **Orchestration:** Pass the alert information to the Python response component.
5. **Validation:** Confirm the source IP, apply exception rules, and check the containment policy.
6. **Response:** Apply an approved firewall action when all conditions are satisfied.
7. **Audit and recovery:** Record the action and maintain a rollback procedure.

**Safety note:** A source IP can be shared by many users or represent a legitimate NAT gateway. Automatic blocking without validation can disrupt legitimate access. Start with alert-only or dry-run mode before enabling containment.

---

## 📸 Screenshots & Evidence

### Screenshot 1: Python Script Code

*Shows the Python script (`vt_automation.py`) used to query the VirusTotal API.*

![Python Script Code](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-7-AI-ML-in-SOC-and-Capstone/Labs/lab16-python-script.png)

### Screenshot 2: Script Output

*Shows the script execution and the VirusTotal reputation data recorded for the IP address.*

![VirusTotal Script Output](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-7-AI-ML-in-SOC-and-Capstone/Labs/lab16-script-output.png)

---

## 💡 Key Takeaways from Module 7

1. **Automation:** Python scripts can reduce repetitive SOC tasks and help analysts process security data more efficiently.
2. **API Integration:** Security APIs enable automated enrichment and help connect tools in a SOC workflow.
3. **SOAR Principles:** Detection, validation, response, audit logging, and recovery should work together.
4. **Detection Engineering:** A reliable brute-force alert requires an appropriate event filter, threshold, grouping strategy, and time window.
5. **Responsible Containment:** Automated firewall actions must be validated, scoped, logged, and reversible.
6. **Capstone Integration:** The project design brings together SIEM monitoring, detection logic, scripting, threat intelligence, and response planning.

---

## ✅ Module 7 Completion Checklist

Mark each item complete only if the activity was actually performed and verified.

- [x] Reviewed AI/ML and automation use cases in SOC operations.
- [x] Developed or tested a Python script for VirusTotal API enrichment.
- [x] Designed and documented the Mini-SOC capstone workflow.
- [x] Documented the lab steps and available screenshot evidence.

**Capstone implementation status:** The architecture and workflow are documented here. Mark live detection and automated firewall containment as implemented only after verifying those steps in the lab.

---

## 📚 References

- [VirusTotal API v3 Documentation](https://docs.virustotal.com/reference/overview)
- [Python Documentation](https://docs.python.org/3/)
- [Requests Library Documentation](https://requests.readthedocs.io/)
- [Splunk Documentation](https://docs.splunk.com/)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [Netfilter / iptables Documentation](https://www.netfilter.org/)

---

**Module 7:** AI/ML in SOC & Capstone Project

**Training Repository:** [SOC Training Program](https://github.com/iftiurhossen11/soc-training-program)
