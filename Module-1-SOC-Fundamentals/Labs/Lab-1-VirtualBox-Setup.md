# Lab 1: VirtualBox Installation & Advanced Configuration

## 🎯 Objective
To deploy a Type-2 Hypervisor (Oracle VirtualBox) on the host machine and configure it to host multiple isolated Virtual Machines (VMs) for the SOC security lab. This lab ensures that the virtualization environment is stable, resource-optimized, and securely isolated from the physical network.

## 🛠️ Tools & Environment Used
- **Hypervisor:** Oracle VM VirtualBox (Version: 7.0.x)
- **Extension Pack:** Oracle VM VirtualBox Extension Pack (for USB 2.0/3.0 and RDP support)
- **Host Operating System:** Windows 11 (64-bit)
- **Guest Operating Systems (VMs):** Kali Linux, Wazuh OVA

## 📝 Detailed Lab Steps & Execution

### Step 1: Hypervisor Installation
1. Downloaded the latest VirtualBox installer and the matching Extension Pack from the official Oracle website.
2. Executed the installer with administrative privileges. Allowed the installation of network interfaces (VirtualBox Host-Only Ethernet Adapter).
3. Installed the Extension Pack by double-clicking the `.vbox-extpack` file and accepting the license agreement.

### Step 2: Resource Configuration & Optimization
1. Opened VirtualBox and navigated to **File -> Preferences -> General**.
2. Verified the "Default Machine Folder" to ensure VMs are saved on a drive with sufficient free space.
3. Checked the **System** settings of the Kali Linux VM to verify resource allocation:
   - Base Memory (RAM): 8192 MB (8 GB) allocated for smooth performance.
   - Processors: 6 CPUs allocated.
   - Enabled Nested Paging and KVM Paravirtualization for better performance.

### Step 3: Virtual Machine Import & Verification
1. Verified that the **Kali Linux** VM (custom build) and the **Wazuh v4.14.9 OVA** (pre-configured SIEM appliance) are successfully imported and visible in the VirtualBox Manager.
2. Confirmed that both VMs are currently in the "Powered Off" state, ready to be booted for subsequent labs.

### Step 4: Network Isolation Setup (Crucial for SOC Lab)
1. Navigated to the Network settings of the Kali Linux VM.
2. Verified that Adapter 1 is enabled and attached to **NAT** (Network Address Translation). 
   - *Note: For future malware analysis labs, this will be changed to "Host-Only Adapter" to prevent any malicious traffic from escaping to the physical network.*
3. Confirmed the "Virtual Cable Connected" option is checked.

## 📸 Screenshots & Evidence

**Screenshot 1: VirtualBox Main Interface**
*This shows the VirtualBox Manager with both Kali Linux and Wazuh VMs successfully imported and powered off.*
![VirtualBox Main Interface](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab1-virtualbox-main.png)

**Screenshot 2: Kali Linux System Settings**
*This proves the resource allocation (8GB RAM, 6 CPUs) to ensure the VM can handle intensive security tools.*
![Kali System Settings](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab1-kali-settings.png)

**Screenshot 3: Kali Linux Network Settings**
*This verifies that the network adapter is configured (NAT mode) and the virtual cable is connected.*
![VM Network Settings](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab1-kali-network.png)

## ✅ Conclusion
VirtualBox was successfully installed, and the Extension Pack was configured. The virtual environment is now fully prepared with the required VMs (Kali Linux and Wazuh). Resource allocation was verified to be optimal, and network settings were confirmed to ensure a safe and isolated testing environment for upcoming SOC modules.
