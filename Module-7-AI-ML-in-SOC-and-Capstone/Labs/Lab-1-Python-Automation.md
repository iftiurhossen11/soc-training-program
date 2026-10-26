# Lab 1: Python Automation for SOC (VirusTotal API Enrichment)

## 🎯 Objective

To automate the process of IoC (Indicator of Compromise) enrichment using Python and the VirusTotal API. This lab demonstrates how SOC analysts can use scripting to quickly assess the reputation of an IP address without manually browsing threat intelligence websites.

## 🛠️ Tools & Environment Used

- **Operating System:** Kali Linux VM
- **Programming Language:** Python 3
- **Library:** `requests`
- **API:** VirusTotal Public API (Free Tier)
- **IoC Tested:** `8.8.8.8`
- **API Version:** VirusTotal API v3

## 📝 Detailed Lab Steps & Execution

### Step 1: Obtaining the VirusTotal API Key

1. Created a free account on [VirusTotal](https://www.virustotal.com/).
2. Navigated to the account profile section and obtained a personal API key.
3. Stored the API key securely instead of hardcoding it in a public repository.
4. Prepared the environment to make authenticated requests to the VirusTotal API.

**Security Note:** API keys are sensitive credentials. They should never be committed to public GitHub repositories, shared in screenshots, or printed in application logs.

### Step 2: Writing the Python Script

1. Created a Python script named `vt_automation.py`.
2. Configured the script to accept an IP address as a command-line argument.
3. Used the Python `requests` library to send an HTTP GET request to the VirusTotal API v3 endpoint:

   `https://www.virustotal.com/api/v3/ip_addresses/{ioc}`

4. Included the API key in the request headers for authentication.
5. Parsed the JSON response to extract the `last_analysis_stats` fields, including:
   - `malicious`
   - `suspicious`
   - `harmless`
6. Displayed the analysis results in the terminal.

### Step 3: Executing the Script

1. Opened the terminal in Kali Linux.
2. Executed the Python script with the test IP address `8.8.8.8`:

   ```bash
   python3 vt_automation.py 8.8.8.8
   ```

3. Successfully retrieved the reported analysis results for Google Public DNS (`8.8.8.8`).

**Observed Output:**

```text
IP Address: 8.8.8.8
Malicious: 0
Suspicious: 0
Harmless: 53
```

These values represent the results recorded during the lab. VirusTotal results may change as security vendors update their analysis.

## 📊 Analysis Results

| Attribute | Result |
|---|---:|
| Tested IP Address | `8.8.8.8` |
| Associated Service | Google Public DNS |
| Malicious Detections | 0 |
| Suspicious Detections | 0 |
| Harmless Detections | 53 |

The observed results did not report malicious or suspicious detections for the tested IP address. However, these values do not guarantee that an IP address is completely safe, and they should be interpreted in the context of the analysis timestamp and available intelligence.

## 📸 Screenshots & Evidence

### Screenshot 1: Python Script Code

This screenshot shows the Python script (`vt_automation.py`) used to query the VirusTotal API and extract IP reputation information.

**Image Preview:**

![Python VirusTotal API Automation Script](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-7-AI-ML-in-SOC-and-Capstone/Labs/lab16-python-script.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-7-AI-ML-in-SOC-and-Capstone/Labs/lab16-python-script.png

### Screenshot 2: Script Output

This screenshot shows the script execution and the reported VirusTotal reputation data for the IP address `8.8.8.8`.

**Image Preview:**

![VirusTotal API Automation Script Output](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-7-AI-ML-in-SOC-and-Capstone/Labs/lab16-script-output.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-7-AI-ML-in-SOC-and-Capstone/Labs/lab16-script-output.png

## 🔍 API Endpoint Summary

**VirusTotal API v3 — IP Address Report**

```text
GET https://www.virustotal.com/api/v3/ip_addresses/{ioc}
```

**Example test IP:**

```text
8.8.8.8
```

**Purpose:**

Retrieve the VirusTotal report for an IP address and extract available reputation statistics from the JSON response.

## ✅ Conclusion

Successfully developed and executed a Python script to automate IoC enrichment using the VirusTotal API. This lab demonstrated how to accept an IP address as a command-line argument, send an authenticated API request, parse a JSON response, and display relevant threat intelligence statistics.

Automating these steps can reduce repetitive manual work and help SOC analysts enrich indicators more efficiently during alert triage and incident investigation. The same approach can be extended to support larger workflows and integrations with Security Orchestration, Automation, and Response (SOAR) platforms.

The reported results for `8.8.8.8` provided a baseline example of automated IP reputation checking. In production, the script should also handle invalid input, API rate limits, HTTP errors, and missing response fields.

## 🎓 Key Skills Demonstrated

- Python scripting for cybersecurity
- VirusTotal API v3 integration
- REST API requests using `requests`
- JSON response parsing
- Command-line argument handling
- Automated IoC enrichment
- API key security practices
- Threat intelligence analysis
- SOC alert triage automation
- SOAR workflow fundamentals
