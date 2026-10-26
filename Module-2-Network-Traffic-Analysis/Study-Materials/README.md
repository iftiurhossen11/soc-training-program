# Module 2: Network Security & Traffic Analysis - Study Materials

This folder contains theoretical notes, protocol references, and study guides for analyzing network traffic and identifying security threats. Network traffic analysis is the core skill of a SOC analyst.

## 📚 Comprehensive Study Topics

### 1. Network Fundamentals & The OSI Model
- **The OSI Model:** Understanding the 7 layers (Application, Presentation, Session, Transport, Network, Data Link, Physical) and how attacks map to each layer.
- **TCP/IP Stack:** The practical implementation of networking. Understanding how data is encapsulated.
- **Ports and Protocols:** Understanding TCP (reliable, connection-oriented) vs UDP (fast, connectionless). Knowing common ports (e.g., 80/HTTP, 443/HTTPS, 445/SMB, 3389/RDP).

### 2. Core Protocols & Threat Hunting
- **DNS (Domain Name System):** How DNS works. Understanding DNS records (A, AAAA, MX, TXT). Threat Hunting for **DNS Tunneling** (using DNS to exfiltrate data).
- **HTTP/HTTPS (Web Traffic):** Understanding GET/POST requests, status codes (200 OK, 404 Not Found, 500 Server Error), and User-Agents. Threat Hunting for malicious web shells.
- **SMB (Server Message Block):** The protocol used for file sharing on Windows. Threat Hunting for lateral movement (e.g., PsExec) and ransomware (e.g., EternalBlue exploit).
- **ARP (Address Resolution Protocol):** How IPs are mapped to MAC addresses. Threat Hunting for ARP Spoofing (Man-in-the-Middle attacks).

### 3. Traffic Analysis Concepts
- **Baselines:** You cannot spot malicious traffic if you don't know what normal traffic looks like. Establishing a network baseline is step one.
- **Indicators of Compromise (IoCs) in Traffic:** 
  - Regular beaconing to a Command & Control (C2) server.
  - Large data transfers (Data Exfiltration).
  - Anomalous port usage.
- **Packet Structures:** Understanding the IP header, TCP header, and payload.

### 4. Tools Overview (Theory)
- **Wireshark:** Deep dive into display filter syntax, coloring rules, and analyzing TCP streams.
- **tcpdump:** Syntax and use cases for capturing traffic on headless Linux servers.
- **NetworkMiner:** How it extracts files and credentials passively from a PCAP file.

### 5. PCAP Analysis Methodology
1.  **Identify the Scope:** What is the time frame and the IPs involved?
2.  **Protocol Hierarchy:** Use Wireshark to see what protocols are predominantly used (e.g., sudden spike in SMB traffic could indicate ransomware).
3.  **Filtering:** Use display filters to isolate malicious traffic.
4.  **Extraction:** Extract artifacts (files, images, credentials).
