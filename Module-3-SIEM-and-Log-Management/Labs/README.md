# Module 3: SIEM & Log Management - Labs

This folder contains the hands-on lab exercises, configurations, and reports for setting up a SIEM and analyzing logs. The primary focus is on using Splunk to collect, search, and alert on security events. These labs simulate the daily tasks of a Tier 1 and Tier 2 SOC Analyst.

## ⚠️ LAB SAFETY WARNING
Splunk will be installed on your isolated Host-Only network. Do not expose the Splunk web interface (port 8000) to the internet, as it may contain sensitive log data. Use strong passwords for the admin account.

---

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Splunk Installation & Basic Configuration
*   **Objective:** Install Splunk Enterprise on a local VM and access the web interface to understand the SIEM architecture.
*   **Tools Required:** Splunk Enterprise (Free trial/Demo version), Windows or Ubuntu Server VM.
*   **Step-by-Step Tasks:**
    1.  Download the Splunk Enterprise installer from the official Splunk website (requires a free account).
    2.  Run the installer. Choose the "Local System" account and set an admin username (e.g., `admin`) and a strong password.
    3.  Launch Splunk. It will open a browser window at `http://localhost:8000` (or the IP of your VM).
    4.  Log in and explore the Splunk Home page. 
    5.  **Verification:** Run your first search in the search bar: `index=_internal | head 10` to verify the installation is working and you can see internal logs.
*   **Expected Outcome:** A fully functional Splunk instance ready to ingest logs from various sources.

### 🔬 Lab 2: Forwarding Windows Event Logs to Splunk (The Core Setup)
*   **Objective:** Configure Splunk Universal Forwarder to send Windows Security and Sysmon logs to the SIEM.
*   **Tools Required:** Splunk Universal Forwarder, Windows 10/11 VM, Splunk Indexer.
*   **Step-by-Step Tasks:**
    1.  Download the Splunk Universal Forwarder on the Windows Victim VM.
    2.  During installation, provide the IP address of your Splunk Indexer (e.g., `192.168.56.20`) and the receiving port (default is 9997).
    3.  After installation, navigate to the configuration folder: `C:\Program Files\SplunkUniversalForwarder\etc\system\local`.
    4.  Edit the `inputs.conf` file (create it if it doesn't exist) to monitor the Security log: 
        ```ini
        [WinEventLog://Security]
        disabled = 0
        index = main
Restart the Splunk Forwarder service in Windows Services.

Go to Splunk Web, click on Settings -> Data Inputs -> Forwarders to verify the forwarder is connected.

Expected Outcome: Windows Security logs (EventCode 4624, 4625) are successfully visible in Splunk when you search index=main.

🔬 Lab 3: Writing Basic SPL Queries (Search Processing Language)
Objective: Learn Search Processing Language (SPL) to filter and analyze logs, which is a daily task for a SOC Analyst.

Tools Required: Splunk Web, Ingested Windows logs.

Step-by-Step Tasks:

Search for failed logins: index=main EventCode=4625.
Find the top 5 users with the most failed logins: index=main EventCode=4625 | top limit=5 user.
Count failed logins by Source IP: index=main EventCode=4625 | stats count by src_ip.
Use the table command to format the output like a spreadsheet: index=main EventCode=4625 | table _time, src_ip, user, EventCode.
Bonus: Search for successful logins (EventCode=4624) and filter out machine accounts using | search user!="*$".
Expected Outcome: Proficiency in basic SPL syntax, using stats, top, and table commands to analyze log data.

🔬 Lab 4: Creating Alerts and Dashboards
Objective: Build a simple SOC dashboard for security monitoring and set up an automated alert for suspicious activity.

Tools Required: Splunk Web.

Step-by-Step Tasks:

Run the search: index=main EventCode=4625.
Click Save As -> Alert.
Set the alert to trigger if the number of results is greater than 5 in a 1-minute window (simulating a brute force attack). Configure it to log the alert to the "Triggered Alerts" tab.
Now, run a search for successful logins: index=main EventCode=4624 | stats count by src_ip.
Click Save As -> Dashboard Panel. Create a new dashboard named "SOC Overview". Add the chart as a pie chart.
Expected Outcome: A functioning alert for brute-force detection and a basic, visual SOC dashboard.

🔬 Lab 5: Analyzing a Simulated Brute Force Attack
Objective: Use the SIEM to detect and investigate a brute force attack originating from the Kali Linux VM.

Tools Required: Kali Linux, Windows VM, Splunk.

Step-by-Step Tasks:

From Kali Linux, perform an SSH or RDP brute force against the Windows VM (using tools like Hydra or Crowbar).
Go to Splunk and search index=main EventCode=4625 to see the flood of failed login attempts.
Identify the attacker's IP (Kali VM) and the targeted username.
Correlate the logs to see if the attacker eventually succeeded (EventCode=4624).
Document the findings in a mini incident report.
Expected Outcome: Real-world experience in using SIEM to detect, correlate, and investigate an active attack.

Note: Detailed lab reports with step-by-step instructions, configuration files (inputs.conf), and screenshots will be added to this repository as they are completed.
