# Module 1: Study Materials - SOC Fundamentals & Lab Architecture

This folder contains the foundational theoretical knowledge required before building a home lab. It covers the organizational structure of a SOC, the importance of log management, and the virtualization concepts needed for a safe testing environment.

## 📚 Comprehensive Study Topics

### 1. The Evolution and Importance of the SOC
- **Why do organizations need a SOC?** Understanding the shift from reactive IT security to proactive, continuous monitoring.
- **The "People, Process, Technology" Triad:** How a SOC relies on skilled analysts (People), well-defined playbooks (Process), and tools like SIEM and EDR (Technology).
- **In-House vs. Outsourced SOC (MSSP):** Understanding the pros and cons of a Managed Security Service Provider (MSSP) versus building an internal security team.

### 2. Incident Response (IR) Lifecycle (NIST SP 800-61)
Understanding how a SOC reacts to an incident is crucial. We follow the NIST framework:
1.  **Preparation:** Establishing the lab, tools, and communication plans.
2.  **Detection & Analysis:** Identifying the incident and determining its scope.
3.  **Containment, Eradication, and Recovery:** Stopping the spread, removing the threat, and restoring systems.
4.  **Post-Incident Activity:** Writing reports and learning from the incident (Lessons Learned).

### 3. Virtualization Concepts for Security Analysts
- **What is a Hypervisor?** Type 1 (Bare-metal, e.g., ESXi) vs. Type 2 (Hosted, e.g., VirtualBox, VMware).
- **Virtual Networking:** Understanding how VirtualBox handles NAT, Bridged, Internal, and Host-Only adapters. **Host-Only** is critical for malware analysis.
- **Snapshots:** The most powerful feature of a VM. How to save a "clean state" and revert to it if a malware sample destroys the OS.
- **Resource Allocation:** How to balance CPU cores, RAM, and Disk space between the Host OS and the VMs so your computer doesn't crash.

### 4. Introduction to Cyber Threat Intelligence (CTI)
- What is an IoC (Indicator of Compromise)? Examples: IP addresses, file hashes (MD5/SHA256), domain names.
- What is a TTP (Tactics, Techniques, and Procedures)? Why understanding attacker behavior is more valuable than just blocking a single IP.
- Introduction to the **MITRE ATT&CK Framework**: A knowledge base of adversary tactics and techniques based on real-world observations.

### 5. Lab Environment Architecture Design
- **The Target (Windows 10/11):** Simulates a corporate endpoint. Will be equipped with Sysmon for deep logging.
- **The Attacker (Kali Linux):** Used to simulate adversarial actions (Nmap, Metasploit).
- **The Defender (Ubuntu Server):** Will host Splunk/ELK to collect and analyze logs.
- **Network Isolation:** Ensuring the lab is a "sandbox" where nothing can escape into the real world.
