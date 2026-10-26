# Module 6: Threat Hunting & CTI - Labs

This folder contains hands-on labs for proactive threat hunting and threat intelligence gathering.

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Intelligence Gathering with Open-Source Tools (OSINT)
*   **Objective:** Use tools to investigate a suspicious IP address or domain.
*   **Tools Required:** VirusTotal, AlienVault OTX, Shodan.
*   **Step-by-Step Tasks:**
    1.  Take a suspicious IP from a previous lab.
    2.  Search the IP on AlienVault OTX to see if it is associated with any known malware families.
    3.  Search the IP on Shodan to see what ports are open.
*   **Expected Outcome:** Enrichment of an IoC with threat intelligence.

### 🔬 Lab 2: Writing and Testing a YARA Rule
*   **Objective:** Create a basic YARA rule to detect a specific malware family.
*   **Tools Required:** YARA, a safe malware sample.
*   **Step-by-Step Tasks:**
    1.  Identify a unique string in a malware sample.
    2.  Write a YARA rule: `rule Detect_Test { strings: $a = "malicious_string" condition: $a }`.
    3.  Run `yara rules.yar sample.exe` to test the rule.
*   **Expected Outcome:** A working YARA rule that detects the sample.

### 🔬 Lab 3: Writing Sigma Rules for SIEM Detection
*   **Objective:** Write a Sigma rule to detect suspicious PowerShell execution.
*   **Tools Required:** Sigma, Splunk.
*   **Step-by-Step Tasks:**
    1.  Write a Sigma rule looking for `powershell.exe` with `-enc` (encoded command) flag.
    2.  Convert the Sigma rule to a Splunk query using `sigmac`.
    3.  Run the query in Splunk against Sysmon logs.
*   **Expected Outcome:** A Sigma rule that can be used across multiple SIEMs.

### 🔬 Lab 4: Hypothesis-Driven Threat Hunt in Splunk
*   **Objective:** Hunt for unusual use of `certutil.exe` in the SIEM.
*   **Tools Required:** Splunk, Sysmon logs.
*   **Step-by-Step Tasks:**
    1.  Search: `index=main EventCode=1 Image="*certutil.exe"`.
    2.  Look for unusual command-line arguments (e.g., `-urlcache -split -f`).
    3.  Document the finding.
*   **Expected Outcome:** Detection of a potential LOLBAS attack.

### 🔬 Lab 5: Mapping an Attack to MITRE ATT&CK
*   **Objective:** Take a real-world threat report and map it to MITRE ATT&CK.
*   **Tools Required:** MITRE ATT&CK Navigator, a threat report (e.g., Mandiant).
*   **Step-by-Step Tasks:**
    1.  Read a threat report (e.g., APT29).
    2.  Identify the tactics and techniques used.
    3.  Map them on the ATT&CK Navigator.
*   **Expected Outcome:** Understanding of how to use the ATT&CK framework.

---
*Note: Detailed lab reports, YARA/Sigma rule syntax, and Splunk queries will be added here.*
