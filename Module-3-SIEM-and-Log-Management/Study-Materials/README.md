# Module 3: SIEM & Log Management - Study Materials

This folder contains detailed theoretical notes, architecture diagrams, and reading materials essential for understanding Security Information and Event Management (SIEM) and Log Management.

## 📚 Topics Covered in this Module

### 1. Fundamentals of Log Management
- **What are Logs?** Understanding event logs, system logs, application logs, and security logs.
- **Log Lifecycle:** Generation, Collection, Aggregation, Parsing, Normalization, Storage, and Retention.
- **Challenges:** Log volume, noise, false positives, and storage constraints.

### 2. SIEM Architecture
- **Core Components:** 
  - **Collectors/Agents:** How logs are forwarded (e.g., Splunk Universal Forwarder, Filebeat).
  - **Indexers:** Where data is parsed and stored for fast searching.
  - **Search Heads:** The interface used by SOC analysts to query data.
- **Correlation Rules:** Writing logic to connect events from different sources (e.g., Firewall block + Windows failed login = Potential Brute Force).

### 3. Key Log Sources for SOC
- **Windows Event Logs:** 
  - *Event ID 4624:* Successful Logon.
  - *Event ID 4625:* Failed Logon.
  - *Event ID 4720:* A user account was created.
- **Linux Logs:** `/var/log/auth.log` (Authentication), `/var/log/syslog`.
- **Network Devices:** Firewall allow/deny logs, IDS/IPS alerts.
- **Web Servers:** Apache/Nginx access logs (HTTP status codes, IPs, User-Agents).

### 4. Introduction to Splunk & SPL
- **Splunk Basics:** Understanding indexes, sourcetypes, and hosts.
- **SPL (Search Processing Language):** 
  - Basic search: `index=main error`
  - Filtering: `index=main EventCode=4625`
  - Statistics: `index=main | stats count by src_ip`

---
*Note: As I progress through the course, I will add more specific notes, cheat sheets, and screenshots of SIEM configurations here.*
