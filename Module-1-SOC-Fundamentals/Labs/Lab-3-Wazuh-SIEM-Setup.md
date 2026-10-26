# Lab 3: Wazuh SIEM Installation & Basic Verification

## 🎯 Objective
To deploy and verify the Wazuh open-source SIEM (Security Information and Event Management) platform. This lab focuses on booting the Wazuh OVA, logging into the server, and verifying the core services are running. This proves the ability to set up a foundational SIEM infrastructure for a SOC.

## 🛠️ Tools & Environment Used
- **Wazuh Manager & Indexer:** v4.14.9
- **Hypervisor:** Oracle VirtualBox
- **OS:** Ubuntu Server (Pre-configured in OVA)
- **Network:** Isolated Host-Only Network

## 📝 Detailed Lab Steps & Execution

### Step 1: Booting the Wazuh OVA
1. Imported the Wazuh OVA into VirtualBox and started the VM.
2. Verified that the Ubuntu Server booted successfully and reached the login screen.
3. Checked the console for the default Wazuh credentials (User: `wazuh-user`, Password: `wazuh`).

### Step 2: Server Login & Verification
1. Logged into the Wazuh server via the terminal using the provided credentials.
2. Upon successful login, verified the Wazuh ASCII art and the system prompt (`wazuh-user@wazuh-server`).
3. Confirmed that the underlying Linux environment is stable and ready for SIEM management.

## 📸 Screenshots & Evidence

**Screenshot 1: Wazuh VM Login Screen**
*This shows the initial boot screen of the Wazuh OVA with the default login credentials.*
![Wazuh Login Screen](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab3-wazuh-login.png)

**Screenshot 2: Wazuh Server Terminal**
*This proves that the user has successfully logged into the Wazuh server and the SIEM services are ready.*
![Wazuh Server Terminal](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-1-SOC-Fundamentals/Labs/lab3-wazuh-terminal.png)

## ✅ Conclusion
The Wazuh OVA was successfully deployed and accessed. The underlying server is functional, providing the foundation for managing agents, ingesting logs, and analyzing security events in the next phase of the SOC lab.
