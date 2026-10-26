# Module 5: Cloud SOC Monitoring

## 🎯 Module Objective
To understand the shared responsibility model in cloud environments (AWS, Azure, GCP), learn how to monitor cloud logs, and detect threats like misconfigurations, unauthorized access, and IAM privilege escalation. Cloud security requires a different mindset than on-premises security.

---

## 📖 1. Cloud Security Fundamentals

### The Shared Responsibility Model:
This is the most critical concept in cloud security.
- **Cloud Provider (AWS/Azure/GCP):** Responsible for "Security **OF** the Cloud" (Physical datacenters, hardware, hypervisor, network infrastructure).
- **Customer (You):** Responsible for "Security **IN** the Cloud" (Data, IAM, configurations, network controls, encryption).

### Major Cloud Providers:
- **AWS (Amazon Web Services):** Market leader. Uses services like CloudTrail, GuardDuty, IAM.
- **Azure (Microsoft):** Strong enterprise integration. Uses Microsoft Sentinel, Entra ID, Activity Logs.
- **GCP (Google Cloud Platform):** Uses Cloud Audit Logs, Security Command Center.

---

## 🛠️ 2. Key Cloud Log Sources for a SOC

### AWS Log Sources:
- **AWS CloudTrail:** Records **all API calls** made in an AWS account. This is the most important log source for security. (e.g., Who deleted the S3 bucket? Who created a new IAM user?).
- **AWS VPC Flow Logs:** Captures IP traffic going to and from network interfaces in a VPC.
- **AWS GuardDuty:** A native threat detection service that uses ML to find malicious activity.

### Azure Log Sources:
- **Azure Activity Log:** Provides insight into subscription-level events (e.g., resource creation, deletion).
- **Azure Entra ID (formerly AD) Sign-in Logs:** Tracks user logins, MFA prompts, and risk detections.
- **Microsoft Defender for Cloud:** Native CSPM (Cloud Security Posture Management) tool.

---

## ⚠️ 3. Common Cloud Threats

### Misconfigured S3 Buckets:
- S3 buckets are used for storage. If configured incorrectly (public access enabled), sensitive data (customer PII, company secrets) can be leaked to the internet.
- **SOC Detection:** Monitor CloudTrail for `PutBucketAcl` events where `AllUsers` is granted access.

### IAM Privilege Escalation:
- Attackers gain initial access (e.g., via a leaked API key) and then try to escalate their privileges to become an Administrator.
- **SOC Detection:** Monitor for `CreatePolicyVersion` or `AttachUserPolicy` events in CloudTrail.

### Compromised Access Keys:
- Developers often hardcode API keys in GitHub repositories. Attackers scrape these and use them to access cloud resources.

---

## 📅 Action Plan for Module 5 (4 Weeks)

*   **Week 1: Cloud Theory & Setup:** Understand the Shared Responsibility Model and create a free-tier AWS account.
*   **Week 2: Log Ingestion:** Enable CloudTrail and learn how to analyze the JSON logs.
*   **Week 3: Cloud SIEM:** Ingest CloudTrail logs into a SIEM (Splunk or Elastic) and write basic queries.
*   **Week 4: Threat Detection:** Use a dataset (e.g., CSE-CIC-IDS2018) or a tool like CloudGoat to simulate a cloud attack and detect it.

---

## ✅ Module 5 Completion Checklist
- [ ] Understand the Shared Responsibility Model.
- [ ] Create a free-tier AWS account and enable MFA.
- [ ] Enable AWS CloudTrail and generate some API calls.
- [ ] Analyze a CloudTrail JSON log.
- [ ] Write a SIEM query to detect unauthorized IAM actions.
- [ ] Audit an S3 bucket for public access.
