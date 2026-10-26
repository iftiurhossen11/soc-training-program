# Module 3: SIEM & Log Management - Study Materials

This folder contains detailed theoretical notes, architecture diagrams, and reading materials essential for understanding Security Information and Event Management (SIEM) and Log Management.

## 📚 Comprehensive Study Topics

### 1. Fundamentals of Log Management
- **What are Logs?** Understanding event logs, system logs, application logs, and security logs.
- **Log Lifecycle:** Generation, Collection, Aggregation, Parsing, Normalization, Storage, and Retention.
- **Challenges:** Log volume, noise, false positives, and storage constraints. Why "Alert Fatigue" is a real problem for SOC analysts.

### 2. SIEM Architecture (Deep Dive)
- **Core Components:** 
  - **Collectors/Agents:** How logs are forwarded (e.g., Splunk Universal Forwarder, Filebeat).
  - **Indexers:** Where data is parsed and stored for fast searching. Understanding Indexes and Sourcetypes.
  - **Search Heads:** The interface used by SOC analysts to query data.
- **Correlation Rules:** Writing logic to connect events from different sources (e.g., Firewall block + Windows failed login = Potential Brute Force).

### 3. Key Log Sources for SOC (Event IDs to Memorize)
- **Windows Event Logs:** 
  - *Event ID 4624:* Successful Logon.
  - *Event ID 4625:* Failed Logon.
  - *Event ID 4720:* A user account was created.
  - *Event ID 4672:* Special privileges assigned to new logon (Admin login).
  - *Event ID 4688:* New process created.
- **Linux Logs:** `/var/log/auth.log` (Authentication), `/var/log/syslog`.
- **Network Devices:** Firewall allow/deny logs, IDS/IPS alerts.
- **Sysmon:** Deep dive into Sysmon Event IDs (e.g., Event ID 1: Process Creation, Event ID 3: Network Connection).

### 4. Introduction to Splunk & SPL
- **Splunk Basics:** Understanding indexes, sourcetypes, and hosts.
- **SPL (Search Processing Language):** 
  - Basic search: `index=main error`
  - Filtering: `index=main EventCode=4625`
  - Statistics: `index=main | stats count by src_ip`
  - Transforming: `index=main | eval user=lower(user) | table _time, user`

### 5. SIEM Use Cases for SOC Analysts
- Detecting Brute Force Attacks.
- Detecting Impossible Travel (logins from two different countries in a short time).
- Detecting Malware Execution (via Sysmon logs).
- Monitoring Privileged User Activity (Admin logins).
