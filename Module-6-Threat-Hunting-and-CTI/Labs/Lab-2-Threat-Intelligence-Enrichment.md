# Lab 2: Threat Intelligence & IoC Enrichment (OSINT)

## 🎯 Objective

To enrich Indicators of Compromise (IoCs) using open-source threat intelligence platforms, including VirusTotal and AlienVault OTX. This lab demonstrates how a SOC analyst can investigate the reputation of an IP address or domain and use threat intelligence to support security alert triage.

## 🛠️ Tools & Environment Used

- **Operating System:** Kali Linux VM
- **Threat Intelligence Platforms:** VirusTotal, AlienVault OTX
- **IoC Tested:** `8.8.8.8`
- **IP Address Purpose:** Google Public DNS — used as a baseline for reputation analysis
- **Analysis Type:** Open-Source Intelligence (OSINT)

## 📝 Detailed Lab Steps & Execution

### Step 1: VirusTotal Analysis

1. Opened [VirusTotal](https://www.virustotal.com/) in the web browser.
2. Searched for the IP address `8.8.8.8`.
3. Reviewed the reported detection ratio of **0/92** and community reputation score of **564**, as recorded during the lab.
4. Examined the **Details** and **Relations** tabs for information about passive DNS records, related URLs, and associated infrastructure.
5. Used the available reputation information to assess whether the IP address had been flagged by the security engines represented in the report.

VirusTotal aggregates security-vendor verdicts and other threat intelligence information. A zero-detection result indicates that none of the engines represented in that particular report flagged the IP address at the time of observation. It does not guarantee that all activity associated with the IP is safe.

### Step 2: AlienVault OTX Analysis

1. Opened [AlienVault OTX](https://otx.alienvault.com/) in the web browser.
2. Searched for the same IP address, `8.8.8.8`.
3. Reviewed the following sections and recorded the reported results:
   - **Pulses:** `0`
   - **Passive DNS:** `500+`
   - **URLs:** `9`
4. Checked the available ownership and reputation information.
5. Observed that the IP address was associated with Google LLC and that no malicious pulses were reported in the examined results.

AlienVault OTX provides community-contributed threat intelligence, including indicators, threat reports, passive DNS information, and related URLs. The number of records provides context for investigation but does not independently determine whether an IP address is malicious.

## 📊 IoC Analysis Summary

| Attribute | Observed Result |
|---|---|
| IoC Type | IPv4 Address |
| IP Address | `8.8.8.8` |
| Associated Organization | Google LLC |
| VirusTotal Detection Ratio | `0/92` |
| VirusTotal Community Reputation | `564` |
| AlienVault OTX Pulses | `0` |
| AlienVault OTX Passive DNS | `500+` |
| AlienVault OTX URLs | `9` |
| Assessment | Baseline IP with no malicious detections reported in the recorded results |

**Note:** These values are the observations supplied for this lab, not independently verified live results. Threat intelligence data can change over time.

## 📸 Screenshots & Evidence

### Screenshot 1: VirusTotal IoC Analysis

This screenshot shows the VirusTotal reputation and detection results for the IP address `8.8.8.8`.

**Image Preview:**

![VirusTotal IoC Analysis](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab15-virustotal-ioc.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab15-virustotal-ioc.png

### Screenshot 2: AlienVault OTX IoC Analysis

This screenshot shows the AlienVault OTX threat intelligence results for the same IP address, including its reported pulses, passive DNS information, and related URLs.

**Image Preview:**

![AlienVault OTX IoC Analysis](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab15-alienvault-ioc.png)

**Direct Image Link:**

https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-6-Threat-Hunting-and-CTI/Labs/lab15-alienvault-ioc.png

## 🔍 Threat Intelligence Resources

- **VirusTotal:** https://www.virustotal.com/
- **AlienVault OTX:** https://otx.alienvault.com/
- **Tested Indicator:** `8.8.8.8`

These resources allow analysts to investigate IP addresses, domains, file hashes, and other indicators when supported by the respective platform.

## ✅ Conclusion

Successfully performed IoC enrichment using VirusTotal and AlienVault OTX. This lab demonstrated how to search for an IP address, review reputation and detection results, examine passive DNS and related URLs, and collect threat intelligence to support security investigations.

The recorded results for `8.8.8.8`, a Google Public DNS address, provided a baseline example for interpreting threat intelligence data. The exercise also highlighted the importance of considering multiple sources when assessing an indicator.

A lack of malicious detections does not guarantee that an indicator is completely safe. In a real SOC environment, analysts should consider the observation time, available intelligence, surrounding network activity, and other evidence before making a final risk assessment.

## 🎓 Key Skills Demonstrated

- Open-Source Intelligence (OSINT)
- Indicator of Compromise (IoC) enrichment
- IP address reputation analysis
- VirusTotal detection and community reputation review
- AlienVault OTX pulse investigation
- Passive DNS and URL relationship analysis
- Threat intelligence correlation
- Security alert triage
- Evidence-based risk assessment
