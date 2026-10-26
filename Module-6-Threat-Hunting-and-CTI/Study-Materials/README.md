# Module 6: Threat Hunting & CTI - Study Materials

This folder contains resources, hunting queries, and CTI frameworks used to proactively search for threats.

## 📚 Comprehensive Study Topics

### 1. MITRE ATT&CK Framework (Deep Dive)
- Understanding the 14 Tactics (e.g., Reconnaissance, Execution, Persistence).
- Mapping specific APT (Advanced Persistent Threat) groups to techniques.
- Using the MITRE ATT&CK Navigator to visualize coverage.

### 2. Hypothesis-Driven Hunting
- How to use the "Pyramid of Pain" to focus on TTPs rather than just IP addresses/hashes.
- Creating hunting hypotheses based on recent CVEs or industry news.
- Documenting the hunt process.

### 3. Threat Intelligence Lifecycle
- **Direction:** What do we need to know?
- **Collection:** Gathering data from OSINT and commercial feeds.
- **Processing:** Converting raw data into usable formats (e.g., STIX/TAXII).
- **Analysis:** Turning data into actionable intelligence.
- **Dissemination:** Sharing intel with SOC teams and management.

### 4. Threat Hunting Tools
- **YARA Rules:** Creating rules to identify and classify malware based on textual or binary patterns.
- **Sigma Rules:** Generic signature format for SIEM systems (write once, use in Splunk, Elastic, etc.).
- **LOLBAS:** Understanding how attackers misuse legitimate Windows tools (e.g., certutil, bitsadmin).

### 5. Common Threat Hunting Scenarios
- Hunting for unusual PowerShell execution.
- Hunting for unauthorized scheduled tasks.
- Hunting for lateral movement (e.g., PsExec).
- Hunting for DNS Tunneling.
