# Module 6: Threat Hunting & CTI - Study Materials

This folder contains resources, hunting queries, and CTI frameworks used to proactively search for threats.

## 📚 Topics Covered in this Module

### 1. MITRE ATT&CK Framework (Deep Dive)
- Understanding the 14 Tactics (e.g., Reconnaissance, Execution, Persistence).
- Mapping specific APT (Advanced Persistent Threat) groups to techniques.

### 2. Hypothesis-Driven Hunting
- How to use the "Pyramid of Pain" (by David Bianco) to focus on TTPs rather than just IP addresses/hashes.
- Creating hunting hypotheses based on recent CVEs or industry news.

### 3. Threat Intelligence Lifecycle
- **Direction:** What do we need to know?
- **Collection:** Gathering data from OSINT and commercial feeds.
- **Processing:** Converting raw data into usable formats (e.g., STIX/TAXII).
- **Analysis:** Turning data into actionable intelligence.
- **Dissemination:** Sharing intel with SOC teams and management.

### 4. Threat Hunting Tools
- **YARA Rules:** Creating rules to identify and classify malware based on textual or binary patterns.
- **Sigma Rules:** Generic signature format for SIEM systems (write once, use in Splunk, Elastic, etc.).
- **LOLBAS (Living Off The Land Binaries and Scripts):** Understanding how attackers misuse legitimate Windows tools (e.g., certutil, bitsadmin).

---
*Note: I will add cheat sheets for creating Sigma rules and mapping hunts to MITRE ATT&CK here.*
