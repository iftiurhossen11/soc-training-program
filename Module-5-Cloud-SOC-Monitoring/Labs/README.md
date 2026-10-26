# Module 5: Cloud SOC Monitoring - Labs

This folder contains hands-on labs for setting up cloud monitoring, analyzing cloud logs, and detecting misconfigurations.

## ⚠️ LAB SAFETY WARNING
All cloud labs will be performed using **Free-Tier accounts**. Ensure billing alerts are set up to avoid unexpected charges. Never upload real company data to these practice accounts.

---

## 🧪 Lab Index & Detailed Breakdown

### 🔬 Lab 1: Setting up a Free-Tier AWS Account & IAM
*   **Objective:** Create an AWS account and secure it.
*   **Tools Required:** AWS Free Tier.
*   **Step-by-Step Tasks:**
    1.  Create an AWS account.
    2.  Enable MFA on the Root account.
    3.  Create an IAM user with AdministratorAccess (for daily use).
    4.  Log out of Root and log in as the IAM user.
*   **Expected Outcome:** A secure AWS environment.

### 🔬 Lab 2: Enabling and Analyzing CloudTrail Logs
*   **Objective:** Enable CloudTrail and analyze API activity.
*   **Tools Required:** AWS Management Console.
*   **Step-by-Step Tasks:**
    1.  Navigate to CloudTrail and create a new Trail.
    2.  Create a new S3 bucket from the console.
    3.  Go to CloudTrail Event History and find the `CreateBucket` event.
    4.  Analyze the JSON log to find the `userIdentity`, `sourceIPAddress`, and `eventTime`.
*   **Expected Outcome:** Understanding of how API calls are recorded in the cloud.

### 🔬 Lab 3: Ingesting Cloud Logs into a SIEM
*   **Objective:** Send CloudTrail logs to a local Splunk instance.
*   **Tools Required:** Splunk, AWS S3, AWS CLI.
*   **Step-by-Step Tasks:**
    1.  Configure Splunk to monitor an S3 bucket (using the Splunk Add-on for AWS).
    2.  Generate some activity in AWS (e.g., create an EC2 instance).
    3.  Search for the activity in Splunk: `index=aws sourcetype=aws:cloudtrail eventName=RunInstances`.
*   **Expected Outcome:** Cloud logs are successfully searchable in the SIEM.

### 🔬 Lab 4: Detecting a Simulated Cloud Attack
*   **Objective:** Simulate an IAM privilege escalation and detect it.
*   **Tools Required:** AWS CLI, Splunk.
*   **Step-by-Step Tasks:**
    1.  Using the AWS CLI, attach an AdministratorAccess policy to a low-privileged IAM user.
    2.  Search CloudTrail logs in Splunk for `AttachUserPolicy`.
    3.  Identify which user performed the action and from what IP.
*   **Expected Outcome:** Detection of a privilege escalation attempt.

### 🔬 Lab 5: Auditing an S3 Bucket for Misconfigurations
*   **Objective:** Identify if any S3 bucket is publicly accessible.
*   **Tools Required:** AWS CLI, ScoutSuite.
*   **Step-by-Step Tasks:**
    1.  Create an S3 bucket and make it public.
    2.  Run ScoutSuite against the AWS account.
    3.  Review the report to see if the public bucket is flagged as a high-severity finding.
*   **Expected Outcome:** Understanding of how to audit cloud misconfigurations.

---
*Note: Detailed lab reports, JSON log snippets, and screenshots will be added here.*
