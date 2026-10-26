# Module 7: AI/ML in SOC & Capstone - Labs

This folder contains the practical labs and the final Capstone Project for Module 7.

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Automating Threat Intel with Python
*   **Objective:** Write a Python script that queries the VirusTotal API.
*   **Tools Required:** Python 3, `requests` library, VirusTotal API key.
*   **Step-by-Step Tasks:**
    1.  Install the `requests` library: `pip install requests`.
    2.  Write a script that takes an IP address as input.
    3.  Send a GET request to the VirusTotal API.
    4.  Parse the JSON response and print the number of malicious detections.
*   **Expected Outcome:** A working Python script for IoC enrichment.

### 🔬 Lab 2: Introduction to Machine Learning for Log Analysis
*   **Objective:** Use Python to detect anomalies in network traffic.
*   **Tools Required:** Python, `pandas`, `scikit-learn`.
*   **Step-by-Step Tasks:**
    1.  Load a dataset of network connections (e.g., CIC-IDS2018) into a Pandas DataFrame.
    2.  Use the Isolation Forest algorithm from `scikit-learn` to detect anomalies.
    3.  Visualize the anomalies.
*   **Expected Outcome:** Understanding of how ML models can detect anomalies without signatures.

### 🔬 Lab 3: Implementing a Basic SOAR Playbook
*   **Objective:** Simulate a SOAR playbook.
*   **Tools Required:** Python, `requests`, Slack/Discord webhook.
*   **Step-by-Step Tasks:**
    1.  Write a Python script that triggers when a suspicious login is detected.
    2.  The script should extract the IP, query VirusTotal, and send an alert to a Discord channel.
*   **Expected Outcome:** A basic automation script that mimics a SOAR workflow.

### 🔬 Lab 4: Capstone Project Execution
*   **Objective:** Execute the chosen Capstone Project.
*   **Tools Required:** All tools used in Modules 1-6.
*   **Step-by-Step Tasks:**
    1.  Choose a project (Mini-SOC, Malware Analysis, Threat Hunt, or SOAR).
    2.  Build it in the lab.
    3.  Document every step with screenshots.
*   **Expected Outcome:** A functional project that demonstrates all acquired skills.

### 🔬 Lab 5: Capstone Project Presentation
*   **Objective:** Document the Capstone project findings in a professional report.
*   **Tools Required:** Markdown/Word, PowerPoint.
*   **Step-by-Step Tasks:**
    1.  Write an Executive Summary.
    2.  Document the methodology.
    3.  Present the findings and IoCs.
    4.  Provide recommendations for remediation.
*   **Expected Outcome:** A professional-grade final report and presentation.

---
*Note: All final Capstone Project reports, Python automation scripts, and final documentation will be linked here.*
