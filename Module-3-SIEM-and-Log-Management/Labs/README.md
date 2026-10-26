# Module 3: SIEM & Log Management - Labs

This folder contains hands-on labs for SIEM setup and log analysis. The primary focus is on using Splunk to collect, search, and alert on security events.

## ⚠️ LAB SAFETY WARNING
Splunk will be installed on your isolated Host-Only network. Do not expose the Splunk web interface (port 8000) to the internet.

---

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Splunk Installation & Configuration
*   **Objective:** Install Splunk Enterprise on a local VM and access the web interface.
*   **Tools Required:** Splunk Enterprise (Free trial), Windows/Linux VM.
*   **Step-by-Step Tasks:**
    1.  Download the Splunk Enterprise installer from the official website (requires a free account).
    2.  Run the installer. Set an admin username (e.g., `admin`) and a strong password.
    3.  Launch Splunk. It will open a browser window at `http://localhost:8000`.
    4.  Log in and explore the Splunk Home page. Run your first search: `index=_internal | head 10` to verify the installation.
*   **Expected Outcome:** A fully functional Splunk instance ready to ingest logs.

### 🔬 Lab 2: Forwarding Windows Event Logs to Splunk
*   **Objective:** Configure Splunk Universal Forwarder to send Windows Security logs to the SIEM.
*   **Tools Required:** Splunk Universal Forwarder, Windows 10 VM.
*   **Step-by-Step Tasks:**
    1.  Download the Splunk Universal Forwarder on the Windows VM.
    2.  During installation, provide the IP address of your Splunk Indexer (the server where Splunk is installed).
    3.  After installation, navigate to `C:\Program Files\SplunkUniversalForwarder\etc\system\local`.
    4.  Edit `inputs.conf` to monitor the Security log: 
        ```ini
        [WinEventLog://Security]
        disabled = 0
        index = main
