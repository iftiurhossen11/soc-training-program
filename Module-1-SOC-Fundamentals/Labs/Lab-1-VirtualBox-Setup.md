# Lab 1: VirtualBox Installation & Basic Configuration

## 🎯 Objective
To install Oracle VirtualBox on the host machine and configure the basic settings to host multiple virtual machines for the SOC security lab.

## 🛠️ Tools Used
- Oracle VirtualBox (Version: 7.0.x)
- Oracle VM VirtualBox Extension Pack
- Host OS: Windows 11 (64-bit)

## 📝 Lab Steps & Execution
1. Downloaded the latest VirtualBox installer and the Extension Pack from the official Oracle website.
2. Installed VirtualBox on the Host OS (Windows 11) and installed the Extension Pack for USB support.
3. Verified the Virtual Machines (Kali Linux and Wazuh) are successfully imported and configured in the VirtualBox Manager.
4. Checked the system resources (RAM and CPU) allocated to the Kali Linux VM.
5. Verified the network adapter settings (NAT/Host-Only) to ensure isolation.

## 📸 Screenshots & Evidence

**Screenshot 1: VirtualBox Main Interface**
*This shows the list of Virtual Machines (Kali Linux, Wazuh) installed in the lab environment.*
![VirtualBox Main Interface](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab1-virtualbox-main.png)

**Screenshot 2: Kali Linux System Settings**
*This shows the RAM and CPU allocation for the VM.*
![Kali System Settings](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab1-kali-settings.png)

**Screenshot 3: Kali Linux Network Settings**
*This proves that the VMs are configured with a network adapter for communication.*
![VM Network Settings](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab1-kali-network.png)

## ✅ Conclusion
VirtualBox was successfully installed and configured. The environment is now ready to create virtual machines safely without affecting the host OS. Network isolation was verified for safe security testing.
