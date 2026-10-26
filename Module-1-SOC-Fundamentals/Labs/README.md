# Module 1: Home Lab Setup & Fundamentals - Labs

This folder contains the step-by-step hands-on lab exercises to build a safe, isolated virtual environment. This environment will be the foundation for all future SOC analyst training modules. Each lab includes objectives, required tools, detailed tasks, and expected outcomes.

## ⚠️ LAB SAFETY WARNING
**Never connect a VM containing malware or attack tools to a Bridged network adapter.** Always use **Host-Only** or **Internal Network** to prevent accidental leakage to your physical home network or the internet.

---

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Hypervisor Installation & Configuration
*   **Objective:** Install a Type-2 Hypervisor (Oracle VirtualBox) and configure it for optimal security lab performance.
*   **Tools Required:** Host PC (Windows/Linux/Mac), Oracle VirtualBox Installer, VirtualBox Extension Pack.
*   **Step-by-Step Tasks:**
    1.  Download the latest version of VirtualBox and the matching Extension Pack from the official website.
    2.  Run the installer, allow network interfaces to be created, and install the Extension Pack for USB 2.0/3.0 and RDP support.
    3.  Open VirtualBox -> Preferences -> General. Change the "Default Machine Folder" to a drive with at least 100GB of free space (e.g., `D:\VMs`).
    4.  Go to Preferences -> Network. Verify that no default Host-Only adapters are conflicting with your physical network.
*   **Expected Outcome:** A fully installed VirtualBox environment ready to host multiple VMs without storage issues.

### 🔬 Lab 2: Windows 10/11 VM Creation (The Victim)
*   **Objective:** Deploy the primary victim machine that will simulate a corporate endpoint and generate security logs.
*   **Tools Required:** Windows 10/11 ISO, VirtualBox.
*   **Step-by-Step Tasks:**
    1.  Open VirtualBox and click "New". Name it "Win10-Victim".
    2.  Allocate **4GB RAM** and **50GB Virtual Hard Disk** (VDI, Dynamically allocated).
    3.  Mount the Windows ISO and start the VM. Follow the standard Windows installation process.
    4.  *Post-Installation:* Install VirtualBox Guest Additions for better performance and clipboard sharing.
    5.  *Security Prep:* Temporarily disable Windows Defender Realtime Protection (required later for malware labs) and pause Windows Updates to prevent the VM from auto-restarting during labs.
    6.  Take a snapshot named **"Win10 - Clean Base"**.
*   **Expected Outcome:** A functional Windows VM ready to have Sysmon and Splunk Forwarder installed in later modules.

### 🔬 Lab 3: Kali Linux VM Creation (The Attacker)
*   **Objective:** Deploy the attacker machine used to simulate network attacks and generate malicious traffic.
*   **Tools Required:** Kali Linux VirtualBox Image (OVA) or ISO.
*   **Step-by-Step Tasks:**
    1.  If using the OVA, simply double-click it to import into VirtualBox. If using ISO, create a new VM (2GB RAM, 20GB Disk) and install.
    2.  Set the username and password (e.g., `kali/kali`).
    3.  Open the terminal and run `sudo apt update && sudo apt upgrade -y` to ensure all tools are up to date.
    4.  Take a snapshot named **"Kali - Clean Base"**.
*   **Expected Outcome:** A fully updated Kali Linux VM ready for offensive security tooling.

### 🔬 Lab 4: Network Isolation Setup (Crucial for Safety)
*   **Objective:** Configure a Host-Only network to ensure safe malware analysis and attack simulation. VMs must not be able to reach the internet.
*   **Tools Required:** VirtualBox Network Manager.
*   **Step-by-Step Tasks:**
    1.  In VirtualBox, go to **File -> Tools -> Network Manager**. 
    2.  Go to the **Host-only Networks** tab and click "Create". (A new adapter like `vboxnet0` will appear, usually with IP `192.168.56.1`).
    3.  Go to the settings of both the Windows VM and the Kali VM. Under **Network**, change Adapter 1 to **"Host-only Adapter"** and select `vboxnet0`.
    4.  *Static IP Assignment:* 
        *   Inside Windows: Set IPv4 to `192.168.56.10`, Subnet Mask `255.255.255.0`. (Leave Gateway blank).
        *   Inside Kali: Set IP to `192.168.56.20`.
    5.  *Testing:* Open terminal in Kali and run `ping 192.168.56.10`. Open CMD in Windows and run `ping 192.168.56.20`.
*   **Expected Outcome:** Both VMs can communicate with each other, but neither can reach the internet. This is a safe, isolated sandbox.

### 🔬 Lab 5: Snapshot Management & Disaster Recovery
*   **Objective:** Learn to take, revert, and manage VM snapshots to maintain a clean state when malware destroys the OS.
*   **Tools Required:** VirtualBox Snapshot Manager.
*   **Step-by-Step Tasks:**
    1.  With the Windows VM running, take a snapshot named **"Ready for Module 2"**.
    2.  Simulate a "crash" by deleting a critical system file inside Windows (e.g., delete `C:\Windows\System32\calc.exe`).
    3.  Power off the VM. Right-click the VM -> Snapshots -> Select "Ready for Module 2" -> Click **Restore**.
    4.  Power on the VM and verify the deleted file is back.
*   **Expected Outcome:** Complete understanding of how to maintain a clean lab state, ensuring that future malware analysis doesn't permanently damage the environment.

---
*Note: Detailed lab reports with screenshots of the network configuration, ping tests, and snapshot restorations will be linked in this folder as they are completed.*
