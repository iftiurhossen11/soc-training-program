# Lab 2: Forwarding Linux Logs to Splunk (Log Ingestion)

## 🎯 Objective

To configure Splunk Enterprise to monitor and ingest local Linux authentication logs (`/var/log/auth.log`). This lab demonstrates the ability to configure log sources and verify data ingestion in a SIEM environment.

## 🛠️ Tools & Environment Used

- **Operating System:** Kali Linux VM
- **SIEM Platform:** Splunk Enterprise (v10.0.2)
- **Log Source:** `/var/log/auth.log` (Linux Authentication Log)
- **Sourcetype:** `linux_secure`
- **Index:** `main`

## 📝 Detailed Lab Steps & Execution

### Step 1: Generating Test Logs

1. Opened the terminal in Kali Linux.
2. Manually generated a failed login event to ensure the `auth.log` file contains recent data.

**Command:**

```bash
echo "Oct 26 18:30:00 kali sshd[8888]: Failed password for invalid user hacker from 10.0.2.15 port 5555 ssh2" | sudo tee -a /var/log/auth.log
```

This command appends a sample failed SSH login event to `/var/log/auth.log`. It simulates an authentication failure involving an invalid username and a remote IP address.

### Step 2: Configuring Splunk Data Input

1. Logged into the Splunk Web Interface at `http://localhost:8000`.
2. Navigated to **Settings → Data Inputs → Files & Directories**.
3. Clicked on **New Local File & Directory**.
4. Entered the file path:

   `/var/log/auth.log`

5. Set the **Sourcetype** to `linux_secure`.
6. Selected the **Index** as `main`.
7. Submitted the configuration and verified that Splunk was monitoring the file.

This configuration allows Splunk Enterprise to monitor the specified Linux authentication log file and index the incoming events.

### Step 3: Verifying Log Ingestion via Search

1. Navigated to the **Search & Reporting** app.
2. Executed the following search query with the time range set to **All time**:

```spl
index=main
```

3. Successfully observed **2 events** in the search results, confirming that log data from `/var/log/auth.log` was being ingested.
4. Verified the following event fields:

   - **Host:** `kali`
   - **Source:** `/var/log/auth.log`
   - **Sourcetype:** `linux_secure`

The search results demonstrated that Splunk was receiving and indexing Linux authentication events.

### Step 4: Filtering by Sourcetype

1. Executed the following SPL query in the Search & Reporting app:

```spl
index=main sourcetype=linux_secure
```

2. Verified that the search results were filtered to show only events associated with the `linux_secure` sourcetype.

This filtering technique helps SOC analysts focus on specific log sources during security monitoring and investigation.

## 📸 Screenshots & Evidence

### Screenshot 1: Splunk Search for Linux Logs (`index=main`)

This screenshot shows the successful ingestion of `/var/log/auth.log` into Splunk. The failed password events are visible in the search results.

**Image Preview:**

![Splunk Search for Linux Logs](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab8-splunk-linux-logs.png)

**Direct Image Link:**  
https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab8-splunk-linux-logs.png

### Screenshot 2: Sourcetype Filtering (`sourcetype=linux_secure`)

This screenshot shows the ability to filter Linux authentication logs specifically by the `linux_secure` sourcetype.

**Image Preview:**

![Splunk Linux Secure Sourcetype Filtering](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab8-splunk-linux-secure.png)

**Direct Image Link:**  
https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab8-splunk-linux-secure.png

## 🔍 Search Queries Used

**1. Search all events in the main index:**

```spl
index=main
```

**2. Search only Linux authentication log events:**

```spl
index=main sourcetype=linux_secure
```

These queries demonstrate basic SPL searching and filtering techniques used to investigate security events in a SIEM environment.

## ✅ Conclusion

Successfully configured Splunk Enterprise to monitor and ingest local Linux authentication logs from `/var/log/auth.log`. The lab demonstrated how to generate a sample authentication event, configure a local file data input, select the appropriate sourcetype and index, and verify log ingestion using Search Processing Language (SPL).

The successful retrieval of two events confirmed that log data was available in Splunk during the test. Filtering by `linux_secure` further demonstrated how analysts can narrow search results to a particular log source.

These capabilities are fundamental to Security Operations Center (SOC) Analyst workflows. They provide the foundation for monitoring authentication activity, investigating failed login attempts, identifying suspicious access patterns, and developing security alerts.

## 🎓 Key Skills Demonstrated

- Linux authentication log management
- Generating sample security events
- Splunk Enterprise data input configuration
- Log ingestion and indexing
- Sourcetype and source verification
- Search Processing Language (SPL)
- Security event filtering and investigation
- SIEM fundamentals for SOC Analyst operations
