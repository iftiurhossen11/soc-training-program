# Module 2: Network Security & Traffic Analysis - Labs

This folder contains the hands-on lab exercises, PCAP analysis reports, and network forensic investigations for Module 2. Each lab is designed to simulate real-world SOC analyst tasks.

## ⚠️ LAB SAFETY WARNING
All live traffic captures should be performed on your isolated Host-Only network or on your own physical network with explicit permission. Never capture traffic on a network you do not own.

---

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Wireshark Installation & Interface Familiarization
*   **Objective:** Install Wireshark and understand the GUI, capture interfaces, and basic packet structures.
*   **Tools Required:** Wireshark, Windows/Kali VM.
*   **Step-by-Step Tasks:**
    1.  Download and install Wireshark on your Windows 10 VM.
    2.  Launch Wireshark and select the active network interface (Host-Only adapter).
    3.  Start a capture, wait 10 seconds, and stop it.
    4.  Explore the three panes: Packet List, Packet Details, and Packet Bytes.
    5.  Observe the OSI layers in the Packet Details pane (Frame, Ethernet, IP, TCP/UDP).
*   **Expected Outcome:** A functional Wireshark installation and a basic understanding of how to read a raw packet.

### 🔬 Lab 2: Capturing and Filtering Live Traffic
*   **Objective:** Capture live traffic (e.g., pinging a website or another VM) and apply display filters to isolate specific protocols.
*   **Tools Required:** Wireshark, Kali Linux VM, Windows VM.
*   **Step-by-Step Tasks:**
    1.  Start a capture in Wireshark on the Windows VM.
    2.  From the Kali VM, ping the Windows VM (`ping 192.168.56.10`).
    3.  Stop the capture and apply the filter `icmp`. Observe the Echo Request and Echo Reply packets.
    4.  Start a new capture, browse to a website from Windows, and apply the filter `http`.
    5.  Right-click an HTTP packet -> **Follow -> TCP Stream** to see the raw request and response.
*   **Expected Outcome:** Mastery of basic display filters and the "Follow TCP Stream" feature to reconstruct web traffic.

### 🔬 Lab 3: Analyzing a PCAP File (Simulated Attack)
*   **Objective:** Analyze a pre-captured PCAP file containing a simulated attack.
*   **Tools Required:** Wireshark, PCAP file from Malware-Traffic-Analysis.net.
*   **Step-by-Step Tasks:**
    1.  Download a sample PCAP containing an Nmap port scan or a malware infection.
    2.  Open the PCAP in Wireshark. Go to **Statistics -> Protocol Hierarchy** to understand the traffic composition.
    3.  Filter for `tcp.flags.syn == 1 and tcp.flags.ack == 0` to identify SYN packets (port scans).
    4.  Filter for `dns` to check for suspicious domain lookups (DGA - Domain Generation Algorithms).
    5.  Document the attacker's IP, the victim's IP, and the attack vector.
*   **Expected Outcome:** A written report identifying the attack type, the IoCs, and the timeline of events from the PCAP.

### 🔬 Lab 4: Extracting Artifacts with NetworkMiner
*   **Objective:** Use NetworkMiner to extract credentials, images, and files from a suspicious PCAP.
*   **Tools Required:** NetworkMiner (Windows), PCAP file.
*   **Step-by-Step Tasks:**
    1.  Download and install NetworkMiner on your Windows VM.
    2.  Load the suspicious PCAP file into NetworkMiner.
    3.  Go to the **Files** tab and check for downloaded executables (e.g., `.exe`).
    4.  Go to the **Credentials** tab to see if any plaintext passwords were captured.
    5.  Go to the **Images** tab to see if any images were transferred.
*   **Expected Outcome:** Successful extraction of malicious files and IoCs without manually digging through raw packets.

---
*Note: Detailed lab reports with screenshots of Wireshark filters, TCP streams, and NetworkMiner artifact extractions will be linked in this folder as they are completed.*
