# Module 6: Threat Hunting & Cyber Threat Intelligence (CTI)

## 🎯 Module Objective
To transition from reactive alert monitoring to proactive threat hunting, and to leverage Cyber Threat Intelligence (CTI) to identify hidden adversaries within the network. Threat hunting assumes that an attacker has already bypassed automated defenses.

---

## 📖 1. What is Threat Hunting?

### Definition:
Threat Hunting is a proactive, human-driven process of searching through networks and endpoints to detect and isolate advanced threats that evade existing security solutions (like SIEM or EDR).

### Reactive vs. Proactive:
- **Traditional SOC (Reactive):** Waits for an alert to fire, then investigates.
- **Threat Hunting (Proactive):** The analyst forms a hypothesis (e.g., "Attackers might be using PowerShell to download payloads") and actively searches for evidence, even without an alert.

### The Threat Hunting Process (The Hunting Loop):
1.  **Hypothesis:** Formulate a hypothesis based on threat intel or industry news.
2.  **Investigation:** Use SIEM/EDR to search for evidence supporting the hypothesis.
3.  **Discovery:** Identify malicious activity or anomalies.
4.  **Response & Automation:** Create new detection rules (alerts) to catch this activity automatically in the future.

---

## 🛠️ 2. Cyber Threat Intelligence (CTI)

### Definition:
Evidence-based knowledge about an existing or emerging menace or hazard. It helps the SOC understand *who* is attacking them and *how*.

### Types of Intelligence:
- **Strategic:** High-level, for executives (e.g., trends, geopolitical risks).
- **Tactical:** Focuses on TTPs (Tactics, Techniques, and Procedures) of attackers.
- **Operational:** Details about specific incoming attacks.
- **Technical:** IoCs (IPs, domains, file hashes).

### The Pyramid of Pain (by David Bianco):
This model explains why focusing on TTPs is more valuable than focusing on simple IoCs.
1.  **Hash Values (Trivial):** Easy for attackers to change.
2.  **IP Addresses (Easy):** Easy to change.
3.  **Domain Names (Simple):** Can be changed quickly.
4.  **Network/Host Artifacts (Annoying):** Harder to change.
5.  **Tools (Challenging):** The malware or tools they use.
6.  **TTPs (Tough!):** The actual behavior. If you detect the behavior, the attacker must completely change their methodology.

### Threat Intelligence Platforms & Feeds:
- **Open-Source (OSINT):** AlienVault OTX, MISP, VirusTotal.
- **Commercial:** Recorded Future, CrowdStrike Falcon X.
- **IoC Enrichment:** Automatically checking if an IP address seen in a firewall log is known to be malicious.

---

## 🧪 3. Hunting Tools & Frameworks

### MITRE ATT&CK Framework:
- A globally-accessible knowledge base of adversary tactics and techniques based on real-world observations.
- SOC analysts use this to map alerts and hunts to specific attacker behaviors.

### YARA Rules:
- Used to identify and classify malware based on textual or binary patterns. (e.g., searching for a specific string inside a malicious file).

### Sigma Rules:
- A generic signature format for SIEM systems. Write a rule once, and it can be converted to Splunk, Elastic, or QRadar queries.

### LOLBAS (Living Off The Land Binaries and Scripts):
- Understanding how attackers misuse legitimate Windows tools (e.g., `certutil`, `bitsadmin`, `whoami`) to avoid detection.

---

## 📅 Action Plan for Module 6 (2 Weeks)

*   **Week 1: CTI & OSINT:** Learn how to use VirusTotal, AlienVault OTX, and MISP to enrich IoCs.
*   **Week 2: Hunting in the SIEM:** Formulate hypotheses and hunt for suspicious PowerShell execution and LotL attacks.

---

## ✅ Module 6 Completion Checklist
- [ ] Understand the difference between reactive and proactive defense.
- [ ] Explain the Pyramid of Pain.
- [ ] Map an attack to MITRE ATT&CK.
- [ ] Write a basic YARA rule.
- [ ] Write a basic Sigma rule.
- [ ] Perform a hypothesis-driven hunt in Splunk.
