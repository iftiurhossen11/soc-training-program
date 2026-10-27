# Incident Response Report Template

## 📋 1. Incident Details
- **Incident ID:** [Unique ID, e.g., INC-2026-001]
- **Date & Time of Detection:** [YYYY-MM-DD HH:MM:SS UTC]
- **Analyst:** Md Iftiur Hossen Riyad
- **Severity Level:** [Low / Medium / High / Critical]
- **Status:** [Open / In Progress / Contained / Closed]
- **Affected Systems:** [List IPs, Hostnames, or Users]

## 📝 2. Executive Summary
*Provide a high-level overview of the incident for management. This should be understandable by non-technical stakeholders.*

- **What happened:** [Brief description]
- **Impact:** [What was affected? Data loss? Downtime?]
- **Resolution:** [How was it fixed?]

## 🔍 3. Investigation Timeline
| Time (UTC) | Action Taken | Evidence (Screenshot/Log) |
| :--- | :--- | :--- |
| [HH:MM] | [Initial alert received] | [Splunk Alert ID] |
| [HH:MM] | [Investigation started] | [Search query executed] |
| [HH:MM] | [Containment action taken] | [Firewall rule applied] |

## 🛠️ 4. Tools & Techniques Used
- **SIEM:** Splunk (Queries used: `index=main ...`)
- **Network Analysis:** Wireshark (PCAP analysis)
- **Threat Intelligence:** VirusTotal, AlienVault OTX
- **Endpoint Analysis:** `htop`, `netstat`, Sysmon

## 🎯 5. Root Cause Analysis (RCA)
*Explain the fundamental reason for the incident.*

- **Vulnerability Exploited:** [e.g., Weak SSH password, Unpatched CVE]
- **Attacker TTPs:** [e.g., Brute-force, Phishing, Lateral Movement]
- **MITRE ATT&CK Mapping:** [e.g., T1110 - Brute Force]
  - **Reference:** [MITRE ATT&CK T1110](https://attack.mitre.org/techniques/T1110/)

## ✅ 6. Remediation & Containment Steps
1. [Immediate containment: e.g., Blocked IP 192.168.1.100 using iptables]
2. [Eradication: e.g., Reset compromised passwords]
3. [Recovery: e.g., Restored system from backup]

## 📚 7. Lessons Learned & Recommendations
- **What went well?** [e.g., Alert fired immediately]
- **What needs improvement?** [e.g., Need better logging]
- **Recommendations:** [e.g., Implement MFA, patch systems, update firewall rules]

## 📎 8. Appendices
- [Link to raw logs](https://github.com/iftiurhossen11/soc-training-program)
- [Link to screenshots](https://github.com/iftiurhossen11/soc-training-program)
- [Link to IoC list](https://github.com/iftiurhossen11/soc-training-program)
