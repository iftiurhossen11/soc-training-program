# Lab 1: Threat Hunting with MITRE ATT&CK (Privilege Escalation)

## 🎯 Objective

To proactively hunt for suspicious privilege escalation attempts in a Linux environment using Splunk. This lab demonstrates the ability to search for suspicious command execution patterns and map observed behavior to the MITRE ATT&CK framework, particularly T1068 (Exploitation for Privilege Escalation), when supported by appropriate evidence.

## 🛠️ Tools & Environment Used

- **Operating System:** Kali Linux VM
- **SIEM Platform:** Splunk Enterprise (v10.0.2)
- **Log Source:** `/var/log/auth.log` (Linux Authentication Log)
- **Sourcetype:** `linux_secure`
- **Search Language:** Splunk Search Processing Language (SPL)
- **MITRE ATT&CK Technique:** T1068 – Exploitation for Privilege Escalation

## 📝 Detailed Lab Steps & Execution

### Step 1: Generating Suspicious Logs

1. Opened the terminal in Kali Linux.
2. Manually generated a log entry simulating a user named `hacker` invoking a Bash shell as root through `sudo`.

**Command:**

```bash
echo "Oct 26 21:40:00 kali sudo: hacker : TTY=pts/0 ; PWD=/home/hacker ; USER=root ; COMMAND=/bin/bash" | sudo tee -a /var/log/auth.log
```

This command appends a sample sudo-related event to `/var/log/auth.log`. The event represents a scenario in which the user `hacker` attempts to run `/bin/bash` with root privileges.

**Note:** This is a manually generated test event. It does not prove that a real privilege escalation attempt or exploitation occurred.

### Step 2: Hunting in Splunk

1. Logged into the Splunk Web Interface.
2. Opened the **Search & Reporting** app.
3. Executed the following SPL query to search for events containing the suspicious command pattern:

```spl
index=* sourcetype=linux_secure "COMMAND=/bin/bash"
```

4. Set the Time Range to **All time**.
5. Examined the matching events to identify the sudo command and the requested target user.

This search helps identify logged sudo activity involving a Bash shell. Further investigation is needed to determine whether the activity was authorized or suspicious.

### Step 3: Analyzing Event Details

1. Clicked on the matching log entry to expand the event details.
2. Examined the available event fields.

**Observed Event Details:**

- **USER:** `root`
- **COMMAND:** `/bin/bash`
- **PWD:** `/home/hacker`
- **Process:** `sudo`
- **TTY:** `pts/0`
- **Initiating User:** `hacker`

These fields describe a sudo command requesting a Bash shell with root privileges. The event can be used to investigate privilege-related activity, but it does not establish that an exploit succeeded.

## 📸 Screenshots & Evidence

### Screenshot 1: Threat Hunting Search Results

This screenshot shows the Splunk search results for events containing suspicious-looking sudo commands.

**Image Preview:**

![MITRE ATT&CK Threat Hunting Search Results](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab14-threat-hunting-mitre.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab14-threat-hunting-mitre.png

### Screenshot 2: Event Details

This screenshot shows the event details and the fields extracted from the sudo-related log entry.

**Image Preview:**

![MITRE ATT&CK Threat Hunting Event Details](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab14-threat-hunting-details.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab14-threat-hunting-details.png

## 🔍 Search Query Summary

**Search for sudo events containing a Bash command:**

```spl
index=* sourcetype=linux_secure "COMMAND=/bin/bash"
```

This query searches all accessible indexes for events with the `linux_secure` sourcetype containing the specified command string. Actual results depend on the indexed data, permissions, and selected time range.

## 🛡️ MITRE ATT&CK Mapping

- **Technique ID:** T1068
- **Technique Name:** Exploitation for Privilege Escalation
- **Investigation Focus:** Detecting and investigating suspicious attempts to obtain elevated privileges.

**Important distinction:** Running Bash through `sudo` is not, by itself, evidence of T1068. T1068 specifically concerns exploitation of a vulnerability to elevate privileges. This lab demonstrates searching for suspicious privilege-related activity; mapping the event to T1068 requires additional evidence of exploitation. Depending on the actual behavior observed, other privilege-escalation or command-execution techniques may be more appropriate.

## ✅ Conclusion

Successfully performed a targeted threat-hunting exercise using Splunk to identify a sudo-related event involving a Bash shell requested with root privileges. This lab demonstrated how to generate a controlled test log, search indexed Linux authentication events using SPL, and examine event fields to support a security investigation.

The extracted fields can help analysts investigate privileged command execution, establish an event timeline, correlate related authentication records, and develop detection rules for suspicious sudo activity.

Although the event provides a useful starting point for privilege-escalation investigations, a manually generated log entry does not confirm an actual attack or successful exploitation. Accurate MITRE ATT&CK mapping requires evidence of the behavior associated with the selected technique.

## 🎓 Key Skills Demonstrated

- Threat hunting with Splunk
- Linux authentication log analysis
- Sudo command investigation
- SPL search and filtering
- Privileged command execution analysis
- Event field extraction and interpretation
- MITRE ATT&CK framework mapping
- Security event correlation
- Detection rule development fundamentals
