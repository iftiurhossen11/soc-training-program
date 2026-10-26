# Module 2: Network Security & Traffic Analysis

## 🎯 Module Objective
The primary goal of this module is to build a strong foundation in network protocols, understand how data flows across a network, and learn to capture, filter, and analyze network traffic to detect suspicious or malicious activities. A SOC analyst must understand what normal network traffic looks like to identify anomalies. This module covers the OSI model, TCP/IP stack, deep packet inspection (DPI), and the use of tools like Wireshark and tcpdump.

---

## 📖 1. Network Fundamentals for SOC Analysts

### The OSI Model vs. TCP/IP Model
Understanding how data moves from the Application layer down to the Physical layer is crucial for analyzing network attacks.
*   **Layer 7 - Application:** HTTP, HTTPS, DNS, FTP, SSH (Where most attacks happen).
*   **Layer 4 - Transport:** TCP (Connection-oriented, reliable), UDP (Connectionless, fast). **Ports** are used here.
*   **Layer 3 - Network:** IP Addressing, ICMP (Ping), Routing.
*   **Layer 2 - Data Link:** MAC Addresses, ARP (Address Resolution Protocol) - often used in MITM attacks.

### Key Network Protocols & Their Security Implications:
*   **DNS (Domain Name System):** Translates domain names to IPs. (Used heavily in C2 communication and DNS Tunneling).
*   **HTTP/HTTPS:** Web traffic. (Look for unusual User-Agents, large data transfers, or weird URIs).
*   **DHCP:** Assigns IP addresses. (Look for rogue DHCP servers).
*   **SMB (Server Message Block):** File sharing on Windows. (Look for lateral movement or ransomware activity like EternalBlue).
*   **ARP (Address Resolution Protocol):** Used to map IP to MAC. (Look for ARP Spoofing).

### The TCP 3-Way Handshake & Flags
Understanding how a connection is established is key to spotting port scans.
1.  **SYN:** Client sends a SYN packet to initiate a connection.
2.  **SYN-ACK:** Server responds with SYN-ACK.
3.  **ACK:** Client sends ACK to establish the connection.
*   **SOC Relevance:** An Nmap SYN scan (Stealth Scan) sends a SYN, receives a SYN-ACK, but immediately sends an RST (Reset) instead of an ACK.

---

## 🛠️ 2. Traffic Analysis Tools & Techniques

### Wireshark (Deep Packet Inspection)
- **What is it?** A GUI-based packet analyzer that allows you to see the raw data inside every packet.
- **Display Filters (Crucial for SOC Analysts):**
  - `ip.addr == 192.168.1.10` (Filter by IP)
  - `tcp.port == 80` (Filter by Port)
  - `http.request.method == "POST"` (Filter POST requests)
  - `dns.qry.name contains "malicious"` (Filter DNS queries)
- **Follow TCP Stream:** A powerful feature to reconstruct the entire conversation between a client and a server, revealing exactly what data was sent (e.g., stolen credentials).

### tcpdump (Command Line)
- Used on Linux servers where there is no GUI.
- Command example: `tcpdump -i eth0 -w capture.pcap` (Capture traffic on eth0 and save to a file).

### NetworkMiner (Network Forensics)
- A Network Forensic Analysis Tool (NFAT) used to extract files, images, and credentials from a PCAP file without needing to dig through raw packets.

---

## 🧪 3. Planned Labs for Module 2

*   **Lab 1: Wireshark Installation & Interface Familiarization**
    *   *Objective:* Understand the Wireshark GUI, capture interfaces, and basic packet structures.
*   **Lab 2: Capturing and Filtering Live Traffic**
    *   *Objective:* Capture live traffic (e.g., pinging a website) and apply display filters to isolate specific protocols.
*   **Lab 3: Analyzing a PCAP File (Simulated Attack)**
    *   *Objective:* Analyze a pre-captured PCAP file containing a simulated attack (like an Nmap scan or a malware download).
*   **Lab 4: Extracting Artifacts with NetworkMiner**
    *   *Objective:* Use NetworkMiner to extract credentials, images, and files from a suspicious PCAP.

---

## 📅 Action Plan for Module 2 (4 Weeks)

*   **Week 1: Theory & Protocol Basics:** Understand OSI, TCP/IP, and common protocols (DNS, HTTP, SMB). 
*   **Week 2: Wireshark Mastery:** Install Wireshark and learn to use display filters effectively. 
*   **Week 3: PCAP Analysis:** Download sample PCAPs from Malware-Traffic-Analysis.net and analyze them.
*   **Week 4: Network Forensics:** Use NetworkMiner and tcpdump to extract artifacts from PCAPs.

---

## ✅ Module 2 Completion Checklist
- [ ] Understand OSI and TCP/IP models.
- [ ] Install Wireshark and NetworkMiner.
- [ ] Master basic Wireshark display filters.
- [ ] Capture and analyze live HTTP/DNS traffic.
- [ ] Identify a port scan in a PCAP file.
- [ ] Extract a file from a PCAP using NetworkMiner.
