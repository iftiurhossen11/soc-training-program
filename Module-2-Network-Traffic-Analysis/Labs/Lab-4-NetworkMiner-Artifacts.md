# Lab 4: Extracting Artifacts with NetworkMiner

## 🎯 Objective
To use NetworkMiner, a Network Forensic Analysis Tool (NFAT), to extract files, images, and credentials from a captured PCAP file without manually digging through raw packets. This lab demonstrates the ability to quickly identify and extract valuable artifacts from network traffic.

## 🛠️ Tools & Environment Used
- **Operating System:** Kali Linux VM
- **Tool:** NetworkMiner (v3.2)
- **Dataset:** Malware-Traffic-Analysis.net PCAP file (2026-10-01)

## 📝 Detailed Lab Steps & Execution

### Step 1: Launching NetworkMiner
1. Opened the terminal and installed the required dependencies (`mono-devel`).
2. Downloaded the NetworkMiner zip archive and extracted it to `/opt/`.
3. Launched NetworkMiner with root privileges using the command: `sudo mono /opt/NetworkMiner_*/NetworkMiner.exe`.
4. Verified the GUI loaded successfully.

### Step 2: Loading the PCAP File
1. Navigated to **File -> Open**.
2. Selected the previously downloaded `.pcap` file.
3. Waited for NetworkMiner to parse the packets and reconstruct the network sessions.

### Step 3: Extracting Artifacts
1. Navigated to the **Hosts** tab to view the list of communicating IP addresses and hostnames (e.g., `10.10.1.128`, `8.8.8.8`).
2. Navigated to the **Files** tab to view any files transferred over the network. Observed files such as `.txt`, `.ini`, `.cer`, and `.dll`.
3. Checked the **Images** and **Credentials** tabs for extracted images or plaintext passwords.

## 📸 Screenshots & Evidence

**Screenshot 1: NetworkMiner Hosts Overview**
*This shows the list of hosts and their communication details extracted from the PCAP.*
![NetworkMiner Hosts](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab6-networkminer-hosts.png)

**Screenshot 2: Extracted Files & Artifacts**
*This shows the files that NetworkMiner successfully carved out of the network traffic.*
![NetworkMiner Artifacts](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab6-networkminer-artifacts.png)

## ✅ Conclusion
Successfully used NetworkMiner to extract artifacts from a PCAP file. This tool significantly speeds up network forensics by automating the extraction of files and credentials, allowing SOC analysts to quickly identify stolen data or malware payloads.
