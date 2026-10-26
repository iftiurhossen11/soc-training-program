<div align="center">
  <h1>🛡️ SOC Analyst Training Program - Practical Journey</h1>
  <p><strong>A Comprehensive Hands-On Journey into Security Operations, Threat Detection & Incident Response</strong></p>
  
  <a href="https://iftiurhossen11.github.io/iftiurhossenriyad.github.io/" target="_blank">
    <img src="https://img.shields.io/badge/My_Website-Visit-blue?style=for-the-badge&logo=github" alt="Website">
  </a>
  <a href="https://github.com/iftiurhossen11" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-Profile-black?style=for-the-badge&logo=github" alt="GitHub">
  </a>
</div>

---

## 👨‍💻 About the Analyst

Hi, I am **Md Iftiur Hossen Riyad**. I am a dedicated Cyber Security Engineering undergraduate at the University of Frontier Technology, Bangladesh (UFTB), and the Founder & CEO of MyGenie. 

As a security enthusiast, I believe that true defense comes from understanding both the offense and the environment. This repository serves as my public learning journal for the **SOC Analyst Training Program**. It documents my 6-month journey of mastering defensive security operations, threat hunting, and incident response through 100% hands-on labs.

> *"Security is not a product, but a process. This repository is the proof of my process."*

---

## 🎯 Training Objectives & Goals Achieved

By completing this program, I have successfully achieved the following objectives:
- **Mastered the SIEM:** Became proficient in Splunk and Wazuh for log analysis, searching (SPL), and alerting.
- **Network Forensics:** Analyzed malicious traffic and PCAPs to extract Indicators of Compromise (IoCs) using Wireshark and NetworkMiner.
- **Malware Analysis:** Performed static and dynamic analysis in isolated environments to understand attacker behaviors.
- **Threat Hunting:** Proactively hunted for advanced threats using the MITRE ATT&CK framework and Cyber Threat Intelligence (CTI).
- **Automation:** Used Python and the VirusTotal API to automate IoC enrichment, simulating SOAR (Security Orchestration, Automation, and Response) workflows.

---

## 🗂️ Course Roadmap & Lab Highlights

This training program was divided into 7 comprehensive modules. Below is a detailed summary of the practical labs completed in each module.

### [Module 1: SOC Fundamentals & Home Lab Setup](./Module-1-SOC-Fundamentals)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. VirtualBox Installation & Configuration.
    2. Kali Linux VM Creation & Setup.
    3. Wazuh SIEM Installation & Basic Verification.
*   **Key Skills:** Virtualization, Network Isolation, SIEM Deployment, Linux Fundamentals.

### [Module 2: Network Security & Traffic Analysis](./Module-2-Network-Traffic-Analysis)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. Wireshark Installation & Interface Familiarization.
    2. Capturing and Filtering Traffic (DNS & HTTP).
    3. Analyzing a PCAP File (Simulated Malware Traffic).
    4. Extracting Artifacts with NetworkMiner.
*   **Key Skills:** Deep Packet Inspection (DPI), PCAP Analysis, IoC Extraction, Network Forensics.

### [Module 3: SIEM & Log Management](./Module-3-SIEM-and-Log-Management)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. Splunk Enterprise Installation.
    2. Forwarding Linux Logs (`auth.log`) to Splunk.
    3. Creating Brute Force Detection Alerts in Splunk.
*   **Key Skills:** Splunk SPL (Search Processing Language), Log Ingestion, Alert Engineering, Windows/Linux Event Logs.

### [Module 4: Endpoint Security & Malware Analysis](./Module-4-Endpoint-Security-and-Malware-Analysis)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. Static Malware Analysis (VirusTotal & MalwareBazaar).
    2. Threat Hunting in Splunk (Failed Root Logins).
    3. Dynamic Analysis (Process & Network Monitoring with `htop`/`netstat`).
*   **Key Skills:** Malware Triage, IoC Enrichment, System Monitoring, Threat Hunting.

### [Module 5: Cloud SOC Monitoring](./Module-5-Cloud-SOC-Monitoring)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. Ingesting CSE-CIC-IDS2018 Cloud Dataset into Splunk.
*   **Key Skills:** Cloud Log Analysis, Dataset Ingestion, Handling Large-Scale Data.

### [Module 6: Threat Hunting & CTI](./Module-6-Threat-Hunting-and-CTI)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. Threat Hunting with MITRE ATT&CK (Privilege Escalation).
    2. Threat Intelligence & IoC Enrichment (OSINT using VirusTotal & AlienVault OTX).
*   **Key Skills:** Hypothesis-Driven Hunting, OSINT, Threat Intelligence, MITRE Mapping.

### [Module 7: AI/ML in SOC & Capstone Project](./Module-7-AI-ML-in-SOC-and-Capstone)
*   **Status:** ✅ Completed
*   **Labs Completed:** 
    1. Python Automation for SOC (VirusTotal API Integration).
*   **Key Skills:** Python Scripting, API Integration, SOAR Concepts, Automation.

---

## 🛠️ Technical Tooling & Arsenal

Throughout this training, I have gained hands-on experience with industry-standard defensive security tools:

*   **SIEM & Analytics:** Splunk, Wazuh, ELK Stack
*   **Network Analysis:** Wireshark, tcpdump, NetworkMiner, Zeek (Bro)
*   **Endpoint & Malware Analysis:** FlareVM (Concepts), Procmon, VirusTotal, PEStudio
*   **Threat Intelligence:** MITRE ATT&CK Navigator, AlienVault OTX, MalwareBazaar
*   **Operating Systems:** Kali Linux, Ubuntu Server, Windows 10/11
*   **Scripting & Automation:** Python (Requests, Pandas), Bash
*   **Virtualization:** Oracle VirtualBox

---

## 📅 Methodology & Study Plan

To balance my university studies and my startup, I followed the **Standard Track** for this training program:

- **Duration:** 6 Months 
- **Time Commitment:** 13-15 hours per week
- **My 4-Step Learning Loop:**
  1.  **📖 Theory & Research:** Reading study materials, vendor documentation, and threat reports.
  2.  **🧪 Hands-On Lab:** Executing attacks in my isolated VM lab and capturing the logs.
  3.  **📝 Documentation:** Writing detailed lab reports, extracting IoCs, and taking screenshots.
  4.  **🛡️ Detection Engineering:** Mapping the attack to MITRE ATT&CK and writing Sigma/Splunk detection rules.

---

## ⚠️ Lab Safety & Ethical Guidelines

- **Isolated Environment:** All malware analysis and offensive security labs are strictly conducted in isolated Virtual Machines (VMs) with no internet access (Host-Only Network).
- **Authorized Testing:** Any network scanning, exploitation, or testing is performed *only* on systems I own or within my controlled lab environment.
- **No Live Malware:** I do not upload live, active malware samples to this repository. Only analysis reports, safe IoCs, screenshots, and detection rules are documented here.

---

## 📈 Repository Progress Tracker

- [x] Initial Repository Setup & README configuration
- [x] Created Folder Structures for Modules 1-7
- [x] Finalized Study Plan & Tooling List
- [x] **All Modules:** Detailed Notes, Study Materials, and Lab Indexes Created
- [x] **Module 1:** Complete Home Lab Setup & Notes
- [x] **Module 2:** Complete Network Traffic Analysis & PCAP Labs
- [x] **Module 3:** Complete Splunk Installation & Log Analysis Labs
- [x] **Module 4:** Complete Static/Dynamic Malware Analysis
- [x] **Module 5:** Complete Cloud Log Ingestion Labs
- [x] **Module 6:** Complete Threat Hunting Simulations
- [x] **Module 7:** Complete Python Automation Lab

---

## 💡 Key Learnings & Takeaways

1. **The Power of Logs:** Every attack leaves a trace. Understanding how to read and query logs in a SIEM is the most critical skill for a SOC analyst.
2. **Context is King:** An IP address or a hash means nothing without context. Threat Intelligence (CTI) and OSINT tools are essential for enriching alerts.
3. **Proactive Defense:** Waiting for alerts is not enough. Threat Hunting allows us to find the attackers who have bypassed automated defenses.
4. **Automation is the Future:** As alert volumes grow, automating repetitive tasks using Python and SOAR platforms is the only way to scale SOC operations.

---

## 🤝 Let's Connect!

I am always open to discussions regarding cybersecurity, SOC operations, threat hunting, or potential internship opportunities.

- 🌐 **Website:** <a href="https://iftiurhossen11.github.io/iftiurhossenriyad.github.io/" target="_blank">iftiurhossen11.github.io</a>
- 📧 **Email:** mdiftiurhossenriyad@gmail.com
- 🏢 **Startup:** <a href="https://mygenie-pink.vercel.app" target="_blank">MyGenie (AI-Powered Assistant)</a>

---
<div align="center">
  <i>This repository is actively maintained as part of my continuous learning journey in cybersecurity. Stay tuned for updates!</i>
</div>
