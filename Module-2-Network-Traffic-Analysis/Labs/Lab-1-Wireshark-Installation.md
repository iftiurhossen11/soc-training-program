# Lab 1: Wireshark Installation & Interface Familiarization

## 🎯 Objective
To install and launch Wireshark on the Kali Linux VM, and to understand the basic user interface, including network interfaces and packet details. This is the first step in performing deep packet inspection (DPI) for network forensics and traffic analysis.

## 🛠️ Tools & Environment Used
- **Operating System:** Kali Linux VM
- **Tool:** Wireshark (Pre-installed in Kali Linux)
- **Network Adapter:** eth0 (Active network interface)

## 📝 Detailed Lab Steps & Execution

### Step 1: Launching Wireshark
1. Opened the terminal in Kali Linux.
2. Launched Wireshark with root privileges using the command: `sudo wireshark`.
3. Verified that the Wireshark GUI loaded successfully.

### Step 2: Interface Familiarization
1. Observed the main interface showing available network adapters (e.g., `eth0`).
2. Selected the active interface and started a live packet capture.

### Step 3: Live Packet Capture & Analysis
1. Generated network traffic by executing a `ping 8.8.8.8` command in another terminal.
2. Observed live packets being captured in Wireshark (ICMP, DNS).
3. Selected an ICMP Echo Request packet and explored the three main panes:
   - **Packet List Pane:** Shows the summary of captured packets (Source, Destination, Protocol).
   - **Packet Details Pane:** Shows the OSI layer breakdown (Frame, Ethernet II, Internet Protocol Version 4, Internet Control Message Protocol).
   - **Packet Bytes Pane:** Shows the raw hexadecimal and ASCII data.

## 📸 Screenshots & Evidence

**Screenshot 1: Wireshark Main Interface**
*This shows the list of available network adapters in Wireshark.*
![Wireshark Interface](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab4-wireshark-interface.png)

**Screenshot 2: Live Packet Capture & Details**
*This shows a live capture with a selected ICMP packet, displaying the OSI layer details.*
![Wireshark Capture](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/Lab4-wireshark-capture.png)

## ✅ Conclusion
Wireshark was successfully launched and the interface was explored. Live traffic (ICMP) was successfully captured and analyzed. The ability to capture live traffic and view packet details is a fundamental skill for a SOC analyst when performing network forensics.
