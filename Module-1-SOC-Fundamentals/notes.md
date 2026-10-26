# Module 1: SOC Fundamentals & Home Lab Setup

## 🎯 Module Objective
To understand the core architecture of a Security Operations Center (SOC), the responsibilities of different analyst tiers, and to build a fully functional, isolated virtual home lab for practicing security monitoring and incident response.

---

## 📖 1. SOC Fundamentals (Study Notes)

### What is a SOC?
A Security Operations Center (SOC) is a centralized function within an organization that employs people, processes, and technology to continuously monitor and improve an organization's security posture while preventing, detecting, analyzing, and responding to cybersecurity incidents.

### Core SOC Functions:
*   **Monitoring & Alerting:** 24/7 monitoring of logs, network traffic, and endpoint activities.
*   **Incident Response (IR):** Following the IR lifecycle (Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned).
*   **Threat Intelligence:** Gathering data about current and emerging threats to improve defenses.
*   **Forensics:** Analyzing artifacts to understand how an attack happened.

### SOC Tiers & Roles:
*   **Tier 1 (Alert Analyst / Triage):** Monitors the SIEM dashboard, reviews initial alerts, filters out false positives, and escalates true incidents to Tier 2.
*   **Tier 2 (Incident Responder):** Performs deep-dive investigations, analyzes malware, correlates events across multiple systems, and recommends remediation steps.
*   **Tier 3 (Threat Hunter / Subject Matter Expert):** Proactively searches for hidden threats (Threat Hunting), performs advanced reverse engineering, and creates new detection rules.
*   **SOC Manager:** Handles operations, metrics, team management, and communication with higher management.

### Key SOC Metrics:
*   **MTTD (Mean Time to Detect):** Average time taken to discover a threat.
*   **MTTR (Mean Time to Respond):** Average time taken to contain and resolve a threat.

---

## 🛠️ 2. Home Lab Setup Plan

To practice SOC analyst skills safely, an isolated virtual environment is required. 

### Hardware & Software Requirements:
*   **Host Machine:** Minimum 16GB RAM (8GB is absolute minimum but will be slow), 100GB+ free storage. 
*   **Hypervisor:** Oracle VirtualBox or VMware Workstation Player.

### Virtual Machines (VMs) to be Created:
1.  **Windows 10/11 VM (Victim/Target):** Used to simulate a corporate endpoint. Tools to be installed later: Sysmon, Splunk Universal Forwarder.
2.  **Kali Linux VM (Attacker):** Used to simulate attacks (e.g., Nmap scans, brute force) so we can learn how to detect them.
3.  **Ubuntu Server VM (SIEM/Log Server):** Later in the course, this will host Splunk or Elastic Stack to collect and analyze logs from the Windows VM.

### Network Configuration (Crucial):
*   **Isolated Network:** All VMs will be connected via a "Host-Only" or "Internal Network" adapter. This ensures malware or attack traffic does not leak onto the real internet or the local home network.

---

## 📅 Week-by-Week Action Plan for Module 1

*   **[Week 1] Theory & Lab Planning:** Understand SOC roles, read study materials, and download necessary ISOs (Windows, Kali, Ubuntu).
*   **[Week 2] Hypervisor & VM Setup:** Install VirtualBox, create VMs, and install operating systems.
*   **[Week 3] Network Configuration:** Configure Host-Only networks, take snapshots, and test connectivity between Kali and Windows VMs.
*   **[Week 4] Basic Tool Installation:** Install basic tools (Wireshark on Windows, Nmap on Kali) to ensure the lab is ready for Module 2 (Network Security).

---

## ✅ Lab Progress Checklist
- [ ] Install VirtualBox/VMware on Host OS
- [ ] Download Windows 10/11 ISO
- [ ] Download Kali Linux ISO
- [ ] Create Windows VM and install OS
- [ ] Create Kali Linux VM and install OS
- [ ] Configure Host-Only network for isolation
- [ ] Take a "Clean State" snapshot of both VMs
