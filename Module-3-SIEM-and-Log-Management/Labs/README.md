# Module 3: SIEM & Log Management - Labs

This folder contains the hands-on lab exercises, configurations, and reports for setting up a SIEM and analyzing logs. The primary focus is on using Splunk to collect, search, and alert on security events.

## 🧪 Lab Index

*   **Lab 1: Splunk Installation & Basic Configuration**
    *   *Objective:* Install Splunk Enterprise on a local VM and access the web interface.
    *   *Tasks:* Download Splunk, run the installer, set up an admin account, and access `http://localhost:8000`.

*   **Lab 2: Windows Event Log Forwarding**
    *   *Objective:* Configure Splunk Universal Forwarder to send Windows Security logs to the SIEM.
    *   *Tasks:* Install the forwarder on the Windows 10 VM, configure `inputs.conf` to monitor the Security log, and verify data in Splunk.

*   **Lab 3: Writing Basic SPL Queries**
    *   *Objective:* Learn Search Processing Language (SPL) to filter and analyze logs.
    *   *Tasks:* Search for failed logins (`EventCode=4625`), count events by user, and use `stats` and `table` commands.

*   **Lab 4: Creating Alerts and Dashboards**
    *   *Objective:* Build a simple security dashboard and set up an alert for suspicious activity.
    *   *Tasks:* Create a dashboard panel for failed logins, set up an alert for more than 5 failed logins in 1 minute, and configure email notifications.

*   **Lab 5: Analyzing a Simulated Brute Force Attack**
    *   *Objective:* Use SIEM to detect and investigate a brute force attack.
    *   *Tasks:* Use Kali Linux to perform an SSH brute force (using Hydra), then analyze the failed and successful login logs in Splunk to identify the attacker's IP and compromised account.

---
*Note: Detailed lab reports with step-by-step instructions, configuration files, and screenshots will be added to this repository as they are completed.*
