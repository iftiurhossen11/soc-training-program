# Module 5: Cloud SOC Monitoring

## 🎯 Module Objective
To understand the shared responsibility model in cloud environments (AWS, Azure, GCP), learn how to monitor cloud logs, and detect threats like misconfigurations, unauthorized access, and IAM privilege escalation.

## 📝 Study Notes

### 1. Cloud Security Fundamentals
- **Shared Responsibility Model:** 
  - *Cloud Provider:* Responsible for "Security OF the Cloud" (Physical datacenters, hardware, hypervisor).
  - *Customer:* Responsible for "Security IN the Cloud" (Data, IAM, configurations, network controls).
- **Major Cloud Providers:** AWS (Amazon Web Services), Azure (Microsoft), GCP (Google Cloud Platform).

### 2. Key Cloud Log Sources
- **AWS CloudTrail:** Records all API calls made in an AWS account. (Crucial for detecting unauthorized actions).
- **AWS VPC Flow Logs:** Captures IP traffic going to and from network interfaces in a VPC.
- **Azure Activity Log:** Provides insight into subscription-level events.
- **Azure Entra ID (formerly AD) Sign-in Logs:** Tracks user logins and risk detections.

### 3. Common Cloud Threats
- **Misconfigured S3 Buckets:** Publicly accessible storage leaking sensitive data.
- **IAM Privilege Escalation:** Attackers gaining higher permissions than intended.
- **Compromised Access Keys:** Leaked API keys used to access cloud resources.

### 4. Cloud SIEM & Monitoring
- Ingesting CloudTrail logs into Splunk or Elastic to create alerts (e.g., "Root account login without MFA").
- Using native tools like AWS GuardDuty or Azure Sentinel.

## 📊 Public Datasets
For practice, I will be using the **CSE-CIC-IDS2018** dataset (or similar cloud security datasets) to analyze real-world cloud attack patterns in a lab environment.
