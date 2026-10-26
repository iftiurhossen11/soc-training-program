# Lab 1: Splunk Enterprise Installation & Basic SIEM Configuration

## 🎯 Objective
To deploy Splunk Enterprise, a leading SIEM (Security Information and Event Management) platform, on a Kali Linux Virtual Machine. This lab focuses on the installation process, initial configuration, and verifying the log ingestion pipeline by querying internal Splunk logs.

## 🛠️ Tools & Environment Used
- **Operating System:** Kali Linux VM
- **SIEM Platform:** Splunk Enterprise (v10.0.2)
- **Package Format:** `.deb` (Debian/Ubuntu)
- **Access Method:** Web Browser (http://localhost:8000)
- **Search Language:** SPL (Search Processing Language)

## 📝 Detailed Lab Steps & Execution

### Step 1: Environment Preparation & Download
1. Opened the terminal in Kali Linux.
2. Verified internet connectivity and system architecture (`uname -m`).
3. Used the `wget` command to download the official Splunk Enterprise `.deb` package directly from the Splunk repository:
   ```bash
   wget -O splunk-10.0.2-e2d18b4767e9-linux-amd64.deb "https://download.splunk.com/products/splunk/releases/10.0.2/linux/splunk-10.0.2-e2d18b4767e9-linux-amd64.deb"
   ```
4. Monitored the download progress to ensure the file was not corrupted.

### Step 2: Package Installation
1. Navigated to the directory where the `.deb` file was downloaded.
2. Executed the installation command using `dpkg` with root privileges:
   ```bash
   sudo dpkg -i splunk-10.0.2-e2d18b4767e9-linux-amd64.deb
   ```
3. Verified that the installation completed without dependency errors. The Splunk binaries were installed in `/opt/splunk/`.

### Step 3: Starting Splunk Server & Initial Configuration
1. Navigated to the Splunk binary directory:
   ```bash
   cd /opt/splunk/bin
   ```
2. Started the Splunk server for the first time using the `start` command:
   ```bash
   sudo ./splunk start --accept-license
   ```
3. Accepted the End User License Agreement (EULA).
4. Configured the administrator credentials (Username: `admin`, Password: [Secure Password]).
5. Verified that the Splunk Web Server was listening on port `8000`.
6. Accessed the Splunk Web Interface via `http://localhost:8000` in the browser.

### Step 4: Verifying Log Ingestion via Search
1. Logged into the Splunk Web interface using the admin credentials.
2. Navigated to the Search & Reporting application.
3. Executed a basic search query using SPL (Search Processing Language) to verify internal log ingestion:
   ```spl
   index=_internal | head 10
   ```
4. Analyzed the results: Observed 10 events returned successfully, displaying metadata such as `host=kali`, `source=/opt/splunk/var/log/splunk/health.log`, and `sourcetype=splunkd`.
5. Confirmed that the SIEM is operational and actively ingesting its own internal telemetry.

## 📸 Screenshots & Evidence

### Screenshot 1: Splunk Web Interface Dashboard
This shows the Splunk Enterprise dashboard after successful login, displaying the "Hello, Administrator" welcome screen and the Search & Reporting app.

![Splunk Dashboard](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab7-splunk-dashboard.png)

### Screenshot 2: Internal Log Search & Event Parsing
This shows the search results for `index=_internal | head 10`. It proves the SIEM is successfully parsing logs into fields (host, source, sourcetype) and displaying raw events.

![Splunk Internal Logs](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-3-SIEM-and-Log-Management/Labs/lab7-splunk-internal-logs.png)

## ✅ Conclusion
Splunk Enterprise was successfully installed, configured, and verified on the Kali Linux VM. The web interface is functional, and internal logs are being ingested and parsed correctly into structured fields. This environment is now fully prepared for the next phase: ingesting external log sources (such as Windows Event Logs) for security monitoring, alerting, and threat detection.
