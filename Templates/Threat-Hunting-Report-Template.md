# Threat Hunting Report Template

## 📋 1. Hunt Details

- **Hunt ID:** `HUNT-2026-001`
- **Date:** `YYYY-MM-DD`
- **Analyst:** Md Iftiur Hossen Riyad
- **Hypothesis:**  
  Attackers may be using PowerShell to download or execute payloads without leaving obvious files on disk.

## 🎯 2. Objective

Describe the purpose of the hunt. For example:

- Validate the hunting hypothesis.
- Identify suspicious or previously undetected activity.
- Investigate unusual process execution or network communication.
- Identify opportunities to improve SIEM detection rules.

## 🔍 3. Hunt Methodology

### Data Sources

- Splunk SIEM
- Sysmon Event Logs
- Windows Security Logs
- Firewall Logs
- DNS Logs
- Network Traffic / PCAP

### Search Queries (SPL)

**Example: Search for PowerShell process execution**

```spl
index=main EventCode=1 Image="*powershell.exe"
| table _time host User Image CommandLine ParentImage
| sort - _time
```

**Example: Search for encoded PowerShell commands**

```spl
index=main EventCode=1 Image="*powershell.exe" CommandLine="*-enc*"
| table _time host User CommandLine ParentImage
| sort - _time
```

> These examples assume Sysmon process-creation events are ingested with the relevant fields. Confirm your actual index, sourcetype, and field names before running them.

### Tools Used

- Splunk
- Wireshark
- VirusTotal
- Sysmon
- MITRE ATT&CK

## 📊 4. Findings

Describe the evidence collected during the hunt. Do not label activity malicious without sufficient supporting evidence.

| Finding | Description | Evidence |
|---|---|---|
| Finding 1 | Suspicious PowerShell execution on Host X | Screenshot or relevant log event |
| Finding 2 | Potential beaconing to a suspicious IP address | PCAP or firewall log |
| Finding 3 | Unusual parent-child process relationship | Sysmon process-creation event |

### Evidence Details

- **Affected Host(s):** `[Hostname or asset ID]`
- **Source IP:** `[IP address, if applicable]`
- **Destination IP / Domain:** `[Destination, if applicable]`
- **Timestamp:** `[Timestamp and timezone]`
- **Event ID / Log Reference:** `[Event identifier]`
- **Analyst Notes:** `[Supporting evidence and alternative explanations]`

## 🎯 5. MITRE ATT&CK Mapping

- **Tactic:** Execution — `TA0002`
- **Technique:** Command and Scripting Interpreter: PowerShell — `T1059.001`
- **Reference:** [MITRE ATT&CK — T1059.001](https://attack.mitre.org/techniques/T1059/001/)

**Mapping rationale:** Explain how the observed behavior supports this technique. A PowerShell process alone does not establish malicious activity.

## ✅ 6. Conclusion & Recommendations

- **Was the hypothesis validated?** `[Yes / No / Inconclusive]`
- **Summary of Findings:** `[Describe the evidence and conclusion]`
- **Actions Taken:** `[Investigation, escalation, containment, or none]`
- **New Detection Rules:** `[Rule created or improvement proposed]`
- **Further Investigation Required:** `[Yes / No, with details]`

### Recommended Follow-up Actions

1. Correlate suspicious process execution with network and authentication logs.
2. Verify the affected host and user account with the appropriate team.
3. Preserve relevant evidence before taking disruptive response actions.
4. Create or tune a Splunk detection rule if the evidence supports it.
5. Document false positives, investigation limitations, and lessons learned.

---

**Report Status:** `[In Progress / Completed]`

**Repository:** [SOC Training Program](https://github.com/iftiurhossen11/soc-training-program)
