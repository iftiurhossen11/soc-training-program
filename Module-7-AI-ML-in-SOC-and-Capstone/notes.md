# Module 7: AI/ML in SOC & Capstone Project

## 🎯 Module Objective
To understand how Artificial Intelligence (AI) and Machine Learning (ML) are revolutionizing Security Operations Centers, and to apply all the knowledge gained throughout this program into a final Capstone Project.

---

## 📖 1. Introduction to AI & ML in Cybersecurity

### Traditional SOC vs. AI-Driven SOC:
- **Traditional SOC:** Relies heavily on rule-based detection (e.g., if EventCode=4625 happens 5 times, trigger alert). This leads to alert fatigue and missed zero-day attacks.
- **AI-Driven SOC:** Uses ML models to establish a baseline of "normal" behavior and detects anomalies. It can catch threats that have no known signature.

### Key Machine Learning Concepts:
- **Supervised Learning:** Training models on labeled data (e.g., known malware vs. benign files). Good for classification.
- **Unsupervised Learning:** Finding hidden patterns without labels (e.g., clustering to detect zero-day threats).
- **Natural Language Processing (NLP):** Used for log parsing and threat intelligence extraction from unstructured text.

---

## 🛠️ 2. Use Cases of AI in SOC

### 1. Alert Triage & Noise Reduction:
- AI can automatically group similar alerts together. If 100 alerts fire for the same IP, AI groups them into one incident, reducing the workload for Tier 1 analysts.

### 2. User and Entity Behavior Analytics (UEBA):
- Detecting insider threats by establishing a baseline of normal user behavior. (e.g., If a user who never logs in at 3 AM suddenly logs in and downloads 10GB of data, UEBA flags it).

### 3. Malware Classification:
- Automatically categorizing new malware samples based on their features (PE headers, strings) without human intervention.

### 4. SOAR (Security Orchestration, Automation, and Response):
- Using AI to automate repetitive tasks. (e.g., Automatically querying VirusTotal for an IP, blocking it in the firewall, and sending an email to the user).

---

## ⚠️ 3. Challenges & Limitations of AI in SOC

- **Data Quality:** AI is only as good as the data it is trained on (Garbage In, Garbage Out).
- **Adversarial AI:** Attackers can poison ML models (Data Poisoning) or craft inputs designed to bypass AI detection (Evasion).
- **Explainability:** The "Black Box" problem—it is often hard to explain *why* an AI model flagged an event, which is a problem for incident response.

---

## 🎓 4. Capstone Project Guidelines

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

---

## 📅 Action Plan for Module 7 (2 Weeks)

*   **Week 1: AI/ML Theory & Python:** Understand the basics of AI in security and refresh Python skills for automation.
*   **Week 2: Capstone Execution:** Choose a project, build it in the lab, and document the findings.

---

## ✅ Module 7 Completion Checklist
- [ ] Understand the difference between rule-based and AI-based detection.
- [ ] Explain UEBA and SOAR.
- [ ] Write a Python script to automate an API call (e.g., VirusTotal).
- [ ] Complete the Capstone Project.
- [ ] Write the final report.
