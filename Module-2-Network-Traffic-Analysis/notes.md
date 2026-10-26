# Module 2: Network Security & Traffic Analysis

## 🎯 Module Objective
The objective of this module is to build a strong foundation in network protocols, understand how data flows across a network, and learn to capture, filter, and analyze network traffic to detect suspicious or malicious activities.

---

## 📖 1. Network Fundamentals (Study Notes)

### The OSI Model & TCP/IP Model
Understanding how data moves from the Application layer down to the Physical layer is crucial for a SOC Analyst.
*   **Layer 7 - Application:** HTTP, HTTPS, DNS, FTP, SSH (Where most attacks happen).
*   **Layer 4 - Transport:** TCP (Connection-oriented, reliable), UDP (Connectionless, fast).
*   **Layer 3 - Network:** IP Addressing, ICMP (Ping), Routing.
*   **Layer 2 - Data Link:** MAC Addresses, ARP (Address Resolution Protocol).

### Key Network Protocols for SOC Analysts:
*   **DNS (Domain Name System):** Translates domain names to IPs. (Used heavily in C2 communication and DNS Tunneling).
*   **HTTP/HTTPS:** Web traffic. (Look for unusual User-Agents, large data transfers, or weird URIs).
*   **DHCP:** Assigns IP addresses. (Look for rogue DHCP servers).
*   **SMB (Server Message Block):** File sharing on Windows. (Look for lateral movement or ransomware activity like EternalBlue).

---

## 🛠️ 2. Traffic Analysis Tools & Techniques

### Tools We Will Use:
1.  **Wireshark:** GUI-based packet analyzer. Great for deep packet inspection and protocol dissection.
2.  **tcpdump:** Command-line packet analyzer. Essential for capturing traffic on Linux servers without a GUI.
3.  **NetworkMiner:** Network Forensic Analysis Tool (NFAT) used to extract files and images from PCAP files.

### Key Analysis Techniques:
*   **Display Filters (Wireshark):** 
    *   `ip.addr == 192.168.1.10` (Filter by IP)
    *   `tcp.port == 80` (Filter by Port)
    *   `http.request.method == "POST"` (Filter POST requests)
*   **PCAP Analysis:** Looking for indicators of compromise (IoCs) like beaconing (regular check-ins to a C2 server), port scanning, and data exfiltration.

---

## 🧪 3. Planned Labs for Module 2

*   **[Lab 1: Wireshark Installation & Interface Familiarization](link)**
    *   *Objective:* Understand the Wireshark GUI, capture interfaces, and basic packet structures.
*   **[Lab 2: Capturing and Filtering Traffic](link)**
    *   *Objective:* Capture live traffic (e.g., pinging a website) and apply display filters to isolate specific protocols.
*   **[Lab 3: Analyzing a PCAP File](link)**
    *   *Objective:* Analyze a pre-captured PCAP file containing a simulated attack (like an Nmap scan or a malware download).
*   **[Lab 4: Extracting Artifacts with NetworkMiner](link)**
    *   *Objective:* Use NetworkMiner to extract credentials, images, and files from a suspicious PCAP.

---

## 💡 Key SOC Analyst Takeaways
*   **Baseline is Everything:** You cannot spot malicious traffic if you don't know what normal traffic looks like. 
*   **Follow the Stream:** Wireshark's "Follow TCP Stream" feature is powerful for reconstructing full conversations between an attacker and a victim.
*   **Encrypted Traffic:** Most modern traffic is HTTPS. SOC analysts must look at metadata (SNI, certificate details, JA3 fingerprints) when payloads are encrypted.
