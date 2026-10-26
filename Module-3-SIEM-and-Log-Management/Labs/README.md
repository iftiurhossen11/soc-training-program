
# Module 3: SIEM & Log Management - Labs

This folder contains the hands-on lab exercises, configurations, and reports for setting up a SIEM and analyzing logs. The primary focus is on using Splunk to collect, search, and alert on security events. These labs simulate the daily tasks of a Tier 1 and Tier 2 SOC Analyst.

## ⚠️ LAB SAFETY WARNING

Splunk will be installed on your isolated Host-Only network. Do not expose the Splunk web interface (port 8000) to the internet, as it may contain sensitive log data. Use strong passwords for the admin account.

---

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Splunk Installation & Basic Configuration

- **Objective:** Install Splunk Enterprise on a local VM and access the web interface to understand the SIEM architecture.
- **Tools Required:** Splunk Enterprise (Free trial/Demo version), Windows or Ubuntu Server VM.

**Step-by-Step Tasks:**

1. Download the Splunk Enterprise installer from the official Splunk website (requires a free account).
2. Run the installer. Choose the "Local System" account and set an admin username (e.g., `admin`) and a strong password.
3. Launch Splunk. It will open a browser window at `http://localhost:8000` (or the IP of your VM).
4. Log in and explore the Splunk Home page.
5. **Verification:** Run your first search in the search bar:

   ```spl
   index=_internal | head 10
   ```

   This verifies that the installation is working and internal logs are visible.

**Expected Outcome:** A fully functional Splunk instance ready to ingest logs from various sources.

---

### 🔬 Lab 2: Forwarding Windows Event Logs to Splunk (The Core Setup)

- **Objective:** Configure Splunk Universal Forwarder to send Windows Security and Sysmon logs to the SIEM.
- **Tools Required:** Splunk Universal Forwarder, Windows 10/11 VM, Splunk Indexer.

**Step-by-Step Tasks:**

1. Download the Splunk Universal Forwarder on the Windows VM.
2. During installation, provide the IP address of your Splunk Indexer (e.g., `192.168.56.20`) and the receiving port (default is `9997`).
3. Navigate to the configuration folder:

   ```text
   C:\Program Files\SplunkUniversalForwarder\etc\system\local
   ```

4. Edit the `inputs.conf` file (create it if it doesn't exist) to monitor the Security log.

   **Configuration (`inputs.conf`):**

   ```ini
   [WinEventLog://Security]
   disabled = 0
   index = main
   ```

5. Restart the Splunk Forwarder service in Windows Services.
6. In Splunk Web, go to **Settings → Data Inputs → Forwarders** to verify the forwarder connection.

**Expected Outcome:** Windows Security logs, including EventCode `4624` and `4625`, are visible in Splunk when searching `index=main`, assuming the receiving port, forwarding configuration, and index are configured correctly.

---

### 🔬 Lab 3: Writing Basic SPL Queries (Search Processing Language)

- **Objective:** Learn Search Processing Language (SPL) to filter and analyze logs, a daily task for a SOC Analyst.
- **Tools Required:** Splunk Web, ingested Windows logs.

**Step-by-Step Tasks:**

1. **Search for failed logins:**

   ```spl
   index=main EventCode=4625
   ```

2. **Find the top 5 users with the most failed logins:**

   ```spl
   index=main EventCode=4625
   | top limit=5 user
   ```

3. **Count failed logins by source IP:**

   ```spl
   index=main EventCode=4625
   | stats count by src_ip
   ```

4. **Format the output as a table:**

   ```spl
   index=main EventCode=4625
   | table _time, src_ip, user, EventCode
   ```

5. **Bonus: Search for successful logins and filter out machine accounts:**

   ```spl
   index=main EventCode=4624
   | search user!="*$"
   ```

   Note: Field names can vary depending on the Windows event sourcetype and field extractions. Verify whether your events use fields such as `user`, `src_ip`, `EventCode`, or `EventID`.

**Expected Outcome:** Proficiency in basic SPL syntax, including `stats`, `top`, and `table`, to analyze log data.

---

### 🔬 Lab 4: Creating Alerts and Dashboards

- **Objective:** Build a simple SOC dashboard for security monitoring and configure an alert for suspicious activity.
- **Tools Required:** Splunk Web.

**Step-by-Step Tasks:**

1. Run the search:

   ```spl
   index=main EventCode=4625
   ```

2. Click **Save As → Alert**.
3. Configure the alert to trigger when the number of matching results is greater than 5 within a 1-minute time window.
4. Configure the alert to appear in the **Triggered Alerts** view, if supported by your Splunk version and alert configuration.
5. Run a search for successful logins:

   ```spl
   index=main EventCode=4624
   | stats count by src_ip
   ```

6. Click **Save As → Dashboard Panel**.
7. Create a new dashboard named **SOC Overview**.
8. Add the chart as a pie chart.

**Expected Outcome:** A basic SOC dashboard and a brute-force detection alert that can identify repeated failed-login events.

---

### 🔬 Lab 5: Analyzing a Simulated Brute Force Attack

- **Objective:** Use the SIEM to detect and investigate simulated brute-force activity in an isolated lab.
- **Tools Required:** Kali Linux, Windows VM, Splunk.

**Step-by-Step Tasks:**

1. Prepare an isolated Host-Only lab network with Kali Linux, the Windows VM, and the Splunk instance.
2. Ensure that the relevant Windows audit policies and log collection settings are enabled.
3. Generate controlled authentication-failure events against a test account in your own lab environment. Use only systems and accounts you are authorized to test.
4. In Splunk, search for failed login events:

   ```spl
   index=main EventCode=4625
   ```

5. Identify the source IP address and targeted username by examining the event fields.
6. Search for successful login events:

   ```spl
   index=main EventCode=4624
   ```

7. Correlate the timestamps, source IP addresses, usernames, and authentication outcomes to determine whether any successful login followed the failures.
8. Document the findings in a mini incident report.

**Mini Incident Report Template:**

- **Incident Title:** Simulated Brute-Force Activity
- **Date and Time:** [Insert timestamp]
- **Source IP:** [Insert source IP]
- **Target System:** [Insert target hostname or IP]
- **Targeted Username:** [Insert username]
- **Failed Login Attempts:** [Insert count]
- **Successful Login Detected:** [Yes/No/Unconfirmed]
- **Evidence:** [Insert relevant Splunk events]
- **Analysis:** [Explain the observed activity]
- **Recommended Actions:** [List appropriate defensive measures]

**Expected Outcome:** Practical experience detecting, correlating, and investigating authentication-failure events using a SIEM.

---

## 📁 Repository Structure

```text
Module-3-SIEM-Log-Management/
├── README.md
├── Lab-1-Splunk-Installation/
├── Lab-2-Windows-Log-Forwarding/
│   └── inputs.conf
├── Lab-3-SPL-Queries/
├── Lab-4-Alerts-Dashboards/
├── Lab-5-Brute-Force-Investigation/
└── Reports/
```

## 📝 Lab Documentation Status

Detailed lab reports, configuration files (`inputs.conf`), screenshots, SPL queries, and incident investigation reports will be added to this repository as the labs are completed.
