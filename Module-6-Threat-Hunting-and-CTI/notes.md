# Module 6: Threat Hunting & Cyber Threat Intelligence (CTI)

## 🎯 Module Objective
To transition from reactive alert monitoring to proactive threat hunting, and to leverage Cyber Threat Intelligence (CTI) to identify hidden adversaries within the network.

## 📝 Study Notes

### 1. What is Threat Hunting?
- **Definition:** A proactive, human-driven process of searching through networks and endpoints to detect and isolate advanced threats that evade existing security solutions.
- **Reactive vs. Proactive:** Traditional SOC waits for alerts (reactive). Threat hunting assumes a breach has already occurred (proactive).

### 2. The Threat Hunting Process (The Hunting Loop)
1.  **Hypothesis:** Formulate a hypothesis based on threat intel (e.g., "Attackers might be using PowerShell to download payloads").
2.  **Investigation:** Use SIEM/EDR to search for evidence supporting the hypothesis.
3.  **Discovery:** Identify malicious activity or anomalies.
4.  **Response & Automation:** Create new detection rules (alerts) to catch this activity automatically in the future.

### 3. Cyber Threat Intelligence (CTI)
- **Definition:** Evidence-based knowledge about an existing or emerging menace or hazard.
- **Types of Intelligence:**
  - *Strategic:* High-level, for executives (e.g., trends, geopolitical risks).
  - *Tactical:* Focuses on TTPs (Tactics, Techniques, and Procedures) of attackers.
  - *Operational:* Details about specific incoming attacks.
  - *Technical:* IoCs (IPs, domains, file hashes).
- **Frameworks:** MITRE ATT&CK is the gold standard for mapping threat intel to actual attacks.

### 4. Threat Intelligence Platforms & Feeds
- **Open-Source (OSINT):** AlienVault OTX, MISP, VirusTotal.
- **Commercial:** Recorded Future, CrowdStrike Falcon X.
- **IoC Enrichment:** Automatically checking if an IP address seen in a firewall log is known to be malicious.
