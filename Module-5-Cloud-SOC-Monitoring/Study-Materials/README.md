# Module 5: Cloud SOC Monitoring - Study Materials

This folder contains study materials, architecture diagrams, and references for monitoring security in cloud environments (AWS, Azure, GCP).

## 📚 Comprehensive Study Topics

### 1. Deep Dive into IAM (Identity and Access Management)
- **Users, Groups, and Roles:** Understanding the difference between a user (permanent credentials) and a role (temporary credentials).
- **Policies:** Understanding JSON-based policies and the Principle of Least Privilege.
- **MFA (Multi-Factor Authentication):** Why it is critical to enforce for all cloud users, especially root accounts.

### 2. Cloud Infrastructure Security
- **Network Security Groups (NSG) & Security Groups:** Acting as virtual firewalls. Understanding inbound vs outbound rules.
- **VPC (Virtual Private Cloud):** Isolating resources from the public internet using subnets (Public vs Private).
- **Encryption:** Data at rest (S3, EBS) and Data in transit (TLS/SSL).

### 3. Cloud Forensics & Incident Response
- **Challenges:** Ephemeral resources (servers that are destroyed automatically) make traditional forensics difficult.
- **Solution:** Snapshot the disk (EBS volume) before terminating the instance.
- **Isolation:** How to isolate a compromised EC2 instance by changing its Security Group to deny all traffic.

### 4. Cloud Compliance & Governance
- Understanding compliance frameworks like CIS Benchmarks for AWS/Azure.
- Using tools like AWS Config or Azure Policy to enforce security rules.

### 5. Cloud Threat Hunting
- Hunting for "Impossible Travel" in Azure sign-in logs.
- Hunting for Root account usage in AWS.
- Hunting for S3 bucket policy changes.
