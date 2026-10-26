# Module 3: SIEM & Log Management

## 🎯 Module Objective
The primary objective of this module is to understand how Security Information and Event Management (SIEM) systems work. A SOC analyst spends 80% of their time inside a SIEM. We will learn how logs are collected from various sources, how they are parsed and normalized, and how to write correlation rules to detect security incidents. We will use Splunk as our primary SIEM tool for hands-on practice.

---

## 📖 1. SIEM Fundamentals

### What is a SIEM?
- **SIEM** stands for Security Information and Event Management.
- It is a software solution that aggregates and analyzes activity from many different resources across your entire IT infrastructure.
- **Core Concept:** It collects log data from various sources (Firewalls, Windows, Linux, Applications) and correlates them to detect anomalies that a human might miss.

### The 5 Core Components of a SIEM:
1.  **Log Collection:** Agents (like Splunk Universal Forwarder) or syslog servers collect logs.
2.  **Parsing & Normalization:** The SIEM breaks down the raw log into structured fields (e.g., Source IP, Destination IP, Event ID). Normalization ensures that a "login" from Windows and a "login" from Linux look the same to the SIEM.
3.  **Correlation:** The SIEM looks for relationships between events (e.g., 5 failed logins followed by 1 successful login from the same IP).
4.  **Alerting:** If a correlation rule is triggered, the SIEM generates an alert for the SOC team.
5.  **Dashboards & Reporting:** Visual representation of security posture.

### Common Log Sources for a SOC:
- **Windows Event Logs:** 
  - *Event ID 4624:* Successful Logon.
  - *Event ID 4625:* Failed Logon (Brute Force indicator).
  - *Event ID 4720:* A user account was created.
  - *Event ID 4688:* A new process has been created (requires auditing to be enabled).
- **Linux Logs:** `/var/log/auth.log` (Authentication), `/var/log/syslog`.
- **Network Logs:** Firewall allow/deny logs, IDS/IPS alerts (Suricata/Snort).
- **Cloud Logs:** AWS CloudTrail, Azure Activity Logs.
- **Endpoint Logs:** Sysmon (System Monitor) - the gold standard for deep Windows endpoint visibility.

---

## 🛠️ 2. Introduction to Splunk & SPL

### What is Splunk?
Splunk is one of the industry-leading SIEM platforms. It uses a proprietary search language called **SPL (Search Processing Language)**. Splunk operates on a schema-on-the-fly model, meaning you don't need to define the data structure before ingesting it.

### Splunk Architecture (Basic):
- **Forwarder:** Installed on the endpoint to collect and send logs.
- **Indexer:** Parses the data and stores it in an index (where it is searchable).
- **Search Head:** The web interface where the analyst writes queries.

### SPL (Search Processing Language) Basics:
- **Basic Search:** `index=main error` (Searches for the word "error" in the main index).
- **Filtering:** `index=main EventCode=4625` (Searches for failed logins).
- **Piping (|):** Like Linux, you can pipe commands together. 
  - `index=main EventCode=4625 | stats count by src_ip` (Counts the number of failed logins per source IP).
- **The `table` command:** `index=main EventCode=4625 | table _time, src_ip, user` (Formats the output into a clean table).

---

## 🧪 3. Planned Labs for Module 3

*   **Lab 1: Splunk Installation & Configuration**
    *   *Objective:* Install Splunk Enterprise on a Windows/Linux VM and access the web interface.
*   **Lab 2: Forwarding Windows Event Logs to Splunk**
    *   *Objective:* Configure Splunk Universal Forwarder to send Windows security logs (EventCode 4624/4625) to the SIEM.
*   **Lab 3: Writing Basic SPL Queries**
    *   *Objective:* Learn SPL to filter and analyze logs (e.g., finding failed logins and sorting by IP).
*   **Lab 4: Creating Alerts and Dashboards**
    *   *Objective:* Build a simple dashboard for security monitoring and set up an alert for more than 5 failed logins in 1 minute.

---

## 📅 Action Plan for Module 3 (4 Weeks)

*   **Week 1: SIEM Theory & Installation:** Understand log management concepts and install Splunk Enterprise.
*   **Week 2: Log Ingestion:** Install Splunk Forwarder on the Windows victim VM and verify data ingestion.
*   **Week 3: SPL Mastery:** Spend the week writing different search queries, using `stats`, `eval`, and `table` commands.
*   **Week 4: Alerting & Dashboards:** Build a SOC dashboard and configure email alerts for critical events.

---

## ✅ Module 3 Completion Checklist
- [ ] Understand the core components of a SIEM.
- [ ] List key Windows Event IDs (4624, 4625, 4688).
- [ ] Install Splunk Enterprise.
- [ ] Install and configure Splunk Universal Forwarder on a Windows VM.
- [ ] Write basic SPL queries (`index=`, `stats`, `table`).
- [ ] Create a Splunk Alert for failed logins.
