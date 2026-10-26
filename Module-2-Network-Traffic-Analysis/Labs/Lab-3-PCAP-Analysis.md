# Lab 3: Analyzing a PCAP File (Simulated Attack)

## 🎯 Objective
To analyze a pre-captured PCAP (Packet Capture) file containing simulated malicious traffic. This lab focuses on using Wireshark's statistical tools and display filters to identify Indicators of Compromise (IoCs) and understand attacker behavior.

## 🛠️ Tools & Environment Used
- **Operating System:** Kali Linux VM
- **Tool:** Wireshark
- **Dataset:** Malware-Traffic-Analysis.net PCAP file (2026-10-01)

## 📝 Detailed Lab Steps & Execution

### Step 1: Loading the PCAP File
1. Downloaded the sample PCAP file from a trusted training repository.
2. Opened the `.pcap` file in Wireshark via **File -> Open**.
3. Verified that the file contains 42,497 packets.

### Step 2: Protocol Hierarchy Analysis
1. Navigated to **Statistics -> Protocol Hierarchy**.
2. Analyzed the breakdown of protocols to understand the nature of the traffic. 
3. Observed a high percentage of TCP traffic (97.9%) and noted the presence of SMB, Kerberos, and LDAP protocols, indicating a Windows Active Directory environment.

### Step 3: Filtering for Malicious Indicators
1. Applied the display filter `http.request` to look for suspicious outbound connections.
2. Identified multiple HTTP GET requests originating from the victim IP (10.10.1.128).
3. Analyzed the packet details to extract potential IoCs, such as suspicious URIs and user agents.

## 📸 Screenshots & Evidence

**Screenshot 1: Protocol Hierarchy Statistics**
*This shows the breakdown of protocols captured in the PCAP file.*
![Protocol Hierarchy](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab5-pcap-protocol-hierarchy.webp)

**Screenshot 2: Malicious Traffic Filtering**
*This shows the filtered HTTP traffic revealing suspicious requests from the victim machine.*
![Malicious Traffic](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab5-pcap-malicious-traffic.webp)

## ✅ Conclusion
Successfully analyzed a PCAP file to identify malicious traffic. This lab proves the ability to reconstruct an attack timeline and extract IoCs using Wireshark, a critical skill for SOC analysts.
