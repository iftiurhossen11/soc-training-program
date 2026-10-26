# Module 7: AI/ML in SOC & Capstone Project

## 🎯 Module Objective
To understand how Artificial Intelligence (AI) and Machine Learning (ML) are revolutionizing Security Operations Centers, and to apply all the knowledge gained throughout this program into a final Capstone Project.

## 📝 Study Notes

### 1. Introduction to AI & ML in Cybersecurity
- **Traditional SOC vs. AI-Driven SOC:** Moving from rule-based detection to behavior-based anomaly detection.
- **Key Concepts:** 
  - *Supervised Learning:* Training models on labeled data (e.g., known malware vs. benign files).
  - *Unsupervised Learning:* Finding hidden patterns without labels (e.g., clustering to detect zero-day threats).
- *Natural Language Processing (NLP):* Used for log parsing and threat intelligence extraction.

### 2. Use Cases of AI in SOC
- **Alert Triage:** Reducing false positives by automatically grouping similar alerts.
- **User and Entity Behavior Analytics (UEBA):** Detecting insider threats by establishing a baseline of normal user behavior.
- **Malware Classification:** Automatically categorizing new malware samples based on their features.
- **SOAR (Security Orchestration, Automation, and Response):** Using AI to automate repetitive tasks (e.g., automatically blocking a malicious IP).

### 3. Challenges & Limitations
- **Data Quality:** AI is only as good as the data it is trained on (Garbage In, Garbage Out).
- **Adversarial AI:** Attackers can poison ML models or craft inputs designed to bypass AI detection.
- **Explainability:** The "Black Box" problem—it is often hard to explain why an AI model flagged an event.

---

## 🎓 Capstone Project Guidelines

The Capstone Project is the final assessment of this training program. It requires combining skills from all previous modules.

### Project Options:
1.  **Build a Mini-SOC:** Set up a SIEM (Splunk/ELK), ingest logs from Windows/Linux, simulate an attack (e.g., a brute force or malware execution), and write a full incident response report.
2.  **Malware Analysis Report:** Perform a deep static and dynamic analysis of a real-world malware sample and document the IoCs and MITRE ATT&CK mapping.
3.  **Threat Hunting Exercise:** Formulate a hypothesis, hunt for a specific APT technique in a provided dataset (e.g., CSE-CIC-IDS2018), and present the findings.
4.  **SOAR Automation:** Write a Python script to automate a basic SOC task (e.g., querying VirusTotal for an IP and blocking it in the firewall).

### Deliverables:
- A comprehensive report (PDF or Markdown).
- Screenshots of the lab environment.
- Code scripts (if applicable).
- Final presentation slide deck.
