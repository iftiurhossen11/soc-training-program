# Lab 3: Creating Security Alerts in Splunk (Brute Force Detection)

## 🎯 Objective

To create a scheduled security alert in Splunk Enterprise that triggers when multiple failed login attempts are detected within a short timeframe. This simulates a brute-force attack detection scenario, which is a core use case for a SOC analyst.

## 🛠️ Tools & Environment Used

- **Operating System:** Kali Linux VM
- **SIEM Platform:** Splunk Enterprise (v10.0.2)
- **Log Source:** `/var/log/auth.log` (Linux Authentication Log)
- **Sourcetype:** `linux_secure`

## 📝 Detailed Lab Steps & Execution

### Step 1: Creating the Alert Configuration

1. Logged into Splunk and navigated to **Search & Reporting**.
2. Ran the following search query:

   ```spl
   index=main sourcetype=linux_secure "Failed password"
   ```

3. Clicked **Save As → Alert**.
4. Configured the alert with the following settings:

   - **Title:** `Brute Force Detection - Failed Logins`
   - **Description:** `Alert triggered when more than 5 failed login attempts occur in 1 minute.`
   - **Alert Type:** `Scheduled` (or Real-time for immediate testing)
   - **Trigger Condition:** `search count > 5`
   - **Trigger Actions:** `Add to Triggered Alerts`
   - **Severity:** `Medium`

### Step 2: Generating Test Logs

1. Opened the terminal in Kali Linux.
2. Generated six test failed-login events to test the alert condition.

   ```bash
   for i in {1..6}; do
       echo "Oct 26 19:18:00 kali sshd[9999]: Failed password for invalid user hacker from 10.0.2.15 port 5555 ssh2" | sudo tee -a /var/log/auth.log
   done
   ```

   **Note:** This command appends six test entries to the local authentication log. It does not perform six real SSH login attempts.

### Step 3: Verifying the Triggered Alert

1. Navigated to **Alerts → Triggered Alerts** in Splunk.
2. Checked whether the alert status changed to **Triggered**.
3. Verified the alert details, including the condition `search count > 5` and the six failed-login test events.

## 📸 Screenshots & Evidence

### Screenshot 1: Alert Configuration

This screenshot shows the alert configuration, including the trigger condition (`search count > 5`) and the action to add the alert to Triggered Alerts.

![Splunk Alert Configuration](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab9-splunk-alert-config.png)

[View Screenshot 1 — Alert Configuration](https://github.com/iftiurhossen11/soc-training-program/blob/main/Module-3-SIEM-and-Log-Management/Labs/lab9-splunk-alert-config.png)

### Screenshot 2: Triggered Alert

This screenshot shows the triggered alert in Splunk, indicating that the brute-force detection rule matched the configured condition.

![Splunk Triggered Alert](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab9-splunk-triggered-alert.png)

[View Screenshot 2 — Triggered Alert](https://github.com/iftiurhossen11/soc-training-program/blob/main/Module-3-SIEM-and-Log-Management/Labs/lab9-splunk-triggered-alert.png)

## ✅ Conclusion

Successfully configured a security alert in Splunk Enterprise to detect multiple failed-login events. This lab demonstrates the process of creating detection rules, generating test data, and verifying alert execution—important skills for a Security Operations Center (SOC) analyst.

**Key Skills Demonstrated:**
- Splunk alert configuration
- SPL (Search Processing Language)
- Linux authentication log analysis
- Brute-force detection logic
- Security event monitoring and alert verification
