# Module 5: Cloud SOC Monitoring - Labs

This folder contains hands-on labs for setting up cloud monitoring, analyzing cloud logs, and detecting misconfigurations.

## 🧪 Lab Index

*   **Lab 1: Setting up a Free-Tier AWS Account & IAM**
    *   *Objective:* Create an AWS account, enable MFA for the root user, and create an IAM user with limited permissions.
*   **Lab 2: Enabling and Analyzing CloudTrail Logs**
    *   *Objective:* Enable CloudTrail, perform some actions (like creating an S3 bucket), and analyze the resulting JSON logs to understand how API calls are recorded.
*   **Lab 3: Ingesting Cloud Logs into a SIEM**
    *   *Objective:* Simulate sending CloudTrail logs to a local Splunk instance (or use a cloud-native SIEM like Azure Sentinel/Sumo Logic free tier) and write basic queries to filter events.
*   **Lab 4: Detecting a Simulated Cloud Attack**
    *   *Objective:* Use an attack simulation tool (like CloudGoat or Pacu) or the CSE-CIC-IDS2018 dataset to analyze a scenario where an IAM user's access keys are compromised, and write a detection rule for it.
*   **Lab 5: Auditing an S3 Bucket for Misconfigurations**
    *   *Objective:* Use AWS CLI or tools like `ScoutSuite` to audit S3 bucket permissions and identify if any bucket is publicly accessible.

---
*Note: Detailed lab reports, JSON log snippets, and screenshots will be added here.*
