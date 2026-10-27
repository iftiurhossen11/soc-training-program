# SOC Analyst Training Program — Comprehensive Study Plan

## 🎯 Program Overview

This six-month, self-paced study plan is designed for aspiring Security Operations Center (SOC) Analysts. It combines theoretical learning with hands-on labs to develop practical skills in security monitoring, network traffic analysis, SIEM operations, endpoint security, threat intelligence, and incident response.

The program follows the **Standard Track**, requiring approximately **13–15 hours per week**. Fast Track and Part-Time options are also available to accommodate different schedules.

### Study Tracks

| Track | Duration | Weekly Commitment | Best For |
|---|---|---|---|
| **Fast Track** | 4 months | 20–25 hours | Full-time learners |
| **Standard Track** | 6 months | 13–15 hours | Students and working professionals |
| **Part-Time Track** | 8 months | 5–8 hours | Learners with limited study time |

## 🗓️ Month-by-Month Breakdown — Standard Track

## 📘 Month 1: SOC Fundamentals & Home Lab Setup

**Goal:** Understand SOC operations and build a safe, isolated cybersecurity lab.

| Week | Topics | Practical Activities | Deliverables |
|---|---|---|---|
| Week 1 | SOC tiers, Incident Response lifecycle, MITRE ATT&CK basics | Theory and lab planning | SOC architecture notes |
| Week 2 | Virtualization and VirtualBox | Install Kali Linux | Lab screenshots |
| Week 3 | Network isolation and VM snapshots | Configure a Host-Only network | Network diagram |
| Week 4 | Security tool installation | Install and test Wireshark and Nmap | Module 1 lab report |

**Skills to develop:**
- Understand SOC roles and responsibilities.
- Learn the basics of incident detection and response.
- Build an isolated virtual lab for security testing.
- Understand the purpose of common network analysis tools.

## 📗 Month 2: Network Security & Traffic Analysis

**Goal:** Develop packet analysis and network forensics skills.

| Week | Topics | Practical Activities | Deliverables |
|---|---|---|---|
| Week 5 | Wireshark interface and capture filters | Install and configure Wireshark | Lab 1 report |
| Week 6 | DNS and HTTP display filters | Filter and inspect network traffic | Lab 2 screenshots |
| Week 7 | PCAP analysis and protocol hierarchy | Analyze a provided traffic capture | Lab 3 report |
| Week 8 | NetworkMiner and artifact extraction | Examine hosts and extract available artifacts | Lab 4 report |

**Skills to develop:**
- Capture and filter network traffic.
- Identify common protocols and communication patterns.
- Inspect PCAP files for suspicious behavior.
- Extract and document relevant network artifacts.

## 📙 Month 3: SIEM & Log Management

**Goal:** Deploy Splunk, search security logs, and build basic alerts.

| Week | Topics | Practical Activities | Deliverables |
|---|---|---|---|
| Week 9 | Splunk architecture and installation | Install Splunk Enterprise | Splunk dashboard |
| Week 10 | Linux authentication log ingestion | Configure log inputs | Lab 2 report |
| Week 11 | SPL: search, stats, and table | Write and test SPL queries | SPL query collection |
| Week 12 | Alert creation and brute-force detection | Create and test a detection alert | Lab 3 report |

**Skills to develop:**
- Understand SIEM data ingestion and indexing.
- Search and filter authentication events.
- Use SPL to summarize and investigate events.
- Configure alerts based on defined detection conditions.

## 📕 Month 4: Endpoint Security & Malware Analysis

**Goal:** Investigate suspicious endpoint activity and learn malware analysis fundamentals.

| Week | Topics | Practical Activities | Deliverables |
|---|---|---|---|
| Week 13 | Static analysis using VirusTotal and PEStudio | Examine a safe, authorized sample or its metadata | Malware analysis report |
| Week 14 | Threat hunting and failed root logins | Search authentication events in Splunk | Lab 2 report |
| Week 15 | Process and network monitoring | Practice using `htop`, `netstat`, and related tools | Lab 3 report |
| Week 16 | Incident response documentation | Write an incident report based on lab evidence | Incident response report |

**Skills to develop:**
- Interpret malware reputation and file metadata.
- Investigate suspicious authentication events.
- Monitor processes and network connections.
- Document evidence, impact, and recommended actions.

> **Safety:** Do not execute unknown malware on your everyday operating system. Use an appropriately isolated and controlled analysis environment.

## 📒 Month 5: Cloud SOC Monitoring

**Goal:** Understand cloud security responsibilities and practice analyzing security-related datasets.

| Week | Topics | Practical Activities | Deliverables |
|---|---|---|---|
| Week 17 | Cloud fundamentals and Shared Responsibility Model | Study cloud security concepts | Notes |
| Week 18 | CSE-CIC-IDS2018 dataset ingestion | Import a CSV dataset into Splunk | Lab 1 report |
| Week 19 | Data analysis and SPL | Analyze network traffic records | Search results |
| Week 20 | Cloud security best practices | Review identity, logging, and monitoring concepts | Notes |

**Skills to develop:**
- Understand the Shared Responsibility Model.
- Ingest and search structured security datasets.
- Analyze traffic records in Splunk.
- Recognize the importance of identity management and cloud audit logs.

**Important distinction:** The CSE-CIC-IDS2018 dataset contains network traffic and intrusion-detection data. Importing it into Splunk is useful for security analytics practice, but it is not the same as collecting native cloud audit logs such as AWS CloudTrail or Azure Activity Logs.

## 📓 Month 6: Threat Hunting & Capstone Project

**Goal:** Practice proactive threat hunting and combine the program's skills in a final project.

| Week | Topics | Practical Activities | Deliverables |
|---|---|---|---|
| Week 21 | MITRE ATT&CK-based threat hunting | Investigate suspicious privilege-related activity | Lab 1 report |
| Week 22 | CTI and OSINT | Enrich indicators using VirusTotal and AlienVault OTX | Lab 2 report |
| Week 23 | Capstone project design | Design a Mini-SOC detection and response workflow | Project plan |
| Week 24 | Final presentation and review | Present the methodology, evidence, and findings | Final report |

**Skills to develop:**
- Build and test hunting hypotheses.
- Map observed behavior to MITRE ATT&CK techniques.
- Enrich indicators with threat intelligence.
- Design a SIEM detection and response workflow.
- Communicate technical findings clearly.

## 🏆 Capstone Project: Mini-SOC Threat Detection & Response

The capstone brings together the core skills developed throughout the training program.

**Suggested project:** Detect repeated SSH authentication failures using Splunk and design a controlled response workflow using Python.

### Project Workflow

1. Prepare an isolated lab environment.
2. Collect authentication logs from the target system.
3. Create and test a Splunk detection query.
4. Generate authorized test events in the lab.
5. Validate the source IP and document the findings.
6. Design or implement a controlled response action.
7. Document the evidence, limitations, and recovery procedure.
8. Present the results in a final report.

### Expected Deliverables

- Lab architecture diagram.
- SPL detection query and explanation.
- Screenshots of relevant search results.
- Incident investigation report.
- Python automation code, if implemented.
- Response and rollback documentation.
- Final presentation.

**Verification standard:** Clearly distinguish between a proposed design, a simulated test, and a fully tested implementation. Do not claim automated containment succeeded unless the firewall action was actually verified.

---

## 📚 Recommended Learning Resources

### Books

- *Practical Malware Analysis* — Michael Sikorski and Andrew Honig.
- *The Web Application Hacker's Handbook* — Dafydd Stuttard and Marcus Pinto.

### Websites and Documentation

- [MITRE ATT&CK](https://attack.mitre.org/)
- [Malware-Traffic-Analysis.net](https://www.malware-traffic-analysis.net/)
- [VirusTotal](https://www.virustotal.com/)
- [Splunk Documentation](https://docs.splunk.com/)
- [Wireshark Documentation](https://www.wireshark.org/docs/)
- [Python Documentation](https://docs.python.org/3/)

### YouTube Channels

- John Hammond
- NetworkChuck
- Josh Madakor

Use these resources alongside the hands-on labs. Prefer official documentation when checking current tool behavior, configuration, and syntax.

---

## 📊 Program Progress Tracker

Track your progress throughout the 24-week program.

| Month | Focus Area | Status |
|---|---|---|
| Month 1 | SOC fundamentals and home lab | Not started / In progress / Complete |
| Month 2 | Network security and traffic analysis | Not started / In progress / Complete |
| Month 3 | SIEM and log management | Not started / In progress / Complete |
| Month 4 | Endpoint security and malware analysis | Not started / In progress / Complete |
| Month 5 | Cloud SOC monitoring | Not started / In progress / Complete |
| Month 6 | Threat hunting and capstone | Not started / In progress / Complete |

## ✅ Completion Criteria

- [ ] Complete all seven training modules and at least 16 hands-on labs.
- [ ] Complete the pre-assessment.
- [ ] Pass the final assessment with a score of at least 80%.
- [ ] Complete and document the capstone project.
- [ ] Save relevant screenshots, queries, reports, and project files.
- [ ] Organize the deliverables in the GitHub repository.
- [ ] Review safety, authorization, and evidence-handling practices.

## 📁 Suggested Repository Structure

```text
soc-training-program/
├── Module-1-SOC-Fundamentals/
├── Module-2-Network-Traffic-Analysis/
├── Module-3-SIEM-and-Log-Management/
├── Module-4-Endpoint-Security-and-Malware-Analysis/
├── Module-5-Cloud-SOC-Monitoring/
├── Module-6-Threat-Hunting-and-CTI/
├── Module-7-AI-ML-in-SOC-and-Capstone/
├── Templates/
│   ├── Threat-Hunting-Report-Template.md
│   └── Vulnerability-Assessment-Template.md
├── Assessments/
├── Capstone-Project.md
└── README.md
```

Adapt folder names to match the directories that actually exist in your repository.

---

## 🎓 Final Learning Outcome

Upon completing this study plan, learners should have practical experience with SOC fundamentals, network traffic analysis, SIEM searches and alerts, endpoint investigation, cloud-related security analytics, threat intelligence, and incident response documentation.

The program is intended to build a foundation for further SOC Analyst training. Competence should be demonstrated through reproducible lab work, accurate reporting, and verified results rather than completion checkboxes alone.

**Training Repository:** [SOC Training Program on GitHub](https://github.com/iftiurhossen11/soc-training-program)
