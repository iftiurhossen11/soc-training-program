# Frequently Asked Questions (FAQ)

Welcome to the **SOC Analyst Training Program**! This FAQ answers common questions about SOC analysis, cybersecurity tools, practical labs, and the training roadmap.

## ❓ General Questions

### 1. What is a SOC Analyst?

A Security Operations Center (SOC) Analyst is a cybersecurity professional responsible for monitoring security events, identifying potential threats, investigating suspicious activity, and helping respond to security incidents. SOC Analysts commonly use tools such as SIEM platforms, Endpoint Detection and Response (EDR), and Intrusion Detection Systems (IDS).

### 2. What is the difference between SIEM and EDR?

- **SIEM (Security Information and Event Management):** Collects and analyzes security logs from multiple sources, such as servers, endpoints, and network devices, to identify suspicious activity and support investigations.
- **EDR (Endpoint Detection and Response):** Monitors endpoint activity, including processes, files, and network connections, to detect threats and support investigation and response.

**Key difference:** SIEM provides a broader view across multiple log sources, while EDR focuses on security activity and response at individual endpoints.

### 3. What is the MITRE ATT&CK framework?

MITRE ATT&CK is a knowledge base of adversary tactics and techniques based on real-world observations. It helps SOC Analysts understand attacker behavior, classify observed activity, develop detection strategies, and communicate investigation findings.

### 4. What is the CIA Triad?

The CIA Triad is a fundamental information security model consisting of three principles:

- **Confidentiality:** Ensuring information is accessible only to authorized individuals or systems.
- **Integrity:** Protecting information from unauthorized modification or destruction.
- **Availability:** Ensuring systems and information remain accessible when needed by authorized users.

## 🛠️ Technical Questions

### 5. What is the difference between TCP and UDP?

- **TCP (Transmission Control Protocol):** A connection-oriented protocol that provides reliable, ordered data delivery. It is commonly used by HTTPS, SSH, and FTP.
- **UDP (User Datagram Protocol):** A connectionless protocol that does not guarantee delivery or ordering. It is commonly used for DNS queries, real-time streaming, and many VoIP applications.

**Key difference:** TCP prioritizes reliable, ordered delivery, while UDP has lower protocol overhead and can be useful when speed and low latency are important.

### 6. What is the purpose of a firewall?

A firewall monitors and controls network traffic according to configured security rules. It helps restrict unauthorized communication between networks, devices, and systems. Depending on its capabilities, a firewall may filter traffic based on IP addresses, ports, protocols, applications, or connection state.

### 7. What is a PCAP file?

A PCAP file stores captured network packets for later inspection and analysis. SOC Analysts and incident responders use packet captures to investigate network communication, troubleshoot connectivity issues, and examine suspicious traffic.

Common tools include **Wireshark** and **tcpdump**. Newer capture formats may use PCAPNG.

### 8. What is the difference between a vulnerability and an exploit?

- **Vulnerability:** A weakness in software, hardware, configuration, or a process that could be used to compromise a system.
- **Exploit:** A method, technique, or piece of code that takes advantage of a vulnerability.

**Example:** An unpatched application may contain a vulnerability; an exploit may use that weakness to execute unauthorized actions.

### 9. What is a brute-force attack?

A brute-force attack involves repeatedly attempting passwords or other authentication secrets until a valid one is found. Password spraying and credential stuffing are related but distinct techniques.

Common defensive measures include:

- Enforcing strong, unique passwords.
- Enabling multi-factor authentication (MFA).
- Applying rate limits and appropriate account lockout policies.
- Monitoring repeated authentication failures.
- Alerting on suspicious login patterns and unusual source addresses.

### 10. What is the purpose of VirusTotal?

VirusTotal is an online threat-intelligence service that analyzes submitted files, URLs, domains, and IP addresses using multiple security engines and other data sources.

SOC Analysts can use it to enrich Indicators of Compromise (IoCs) and support investigations. Results should be interpreted carefully: a detection score is not definitive proof of maliciousness, and a lack of detections does not guarantee that an artifact is safe.

**Safety note:** Do not upload confidential, proprietary, or sensitive files to public analysis services unless your organization's policies explicitly permit it.

## 📚 Training Questions

### 11. How long does the training program take?

The program offers three suggested study schedules:

| Track | Duration | Recommended Weekly Study Time |
|---|---|---|
| Standard Track | 6 months | 13–15 hours |
| Fast Track | 4 months | 20–25 hours |
| Part-Time Track | 8 months | 5–8 hours |

These are suggested schedules. Actual completion time depends on your background, practice time, and progress through the labs.

### 12. Do I need prior experience?

No prior professional SOC experience is required. Basic knowledge of networking and operating systems is helpful, but the program starts with fundamental concepts and gradually introduces practical security analysis.

Beginners should be prepared to spend additional time learning Linux commands, networking fundamentals, and basic scripting when needed.

### 13. What tools will I learn?

The program introduces tools and resources used in security monitoring, network analysis, threat investigation, and threat intelligence, including:

- **SIEM and log analysis:** Splunk, with related concepts applicable to other SIEM platforms.
- **Endpoint and security monitoring:** Wazuh concepts and Linux system-monitoring tools.
- **Network analysis:** Wireshark, tcpdump, and NetworkMiner.
- **Threat intelligence:** VirusTotal, MalwareBazaar, and MITRE ATT&CK.
- **Scripting and automation:** Python and security-focused command-line tools.

The exact tools covered depend on the labs and exercises included in each module.

### 14. Is this program hands-on?

The program is designed around practical exercises, tool demonstrations, datasets, and investigation workflows. Its goal is to help learners develop skills through practice rather than theory alone.

Complete the labs in an isolated, authorized environment and document your actual results. Some exercises use sample datasets or simulated events; these should not be presented as evidence of real-world attacks.

### 15. Will I get a certificate?

This is a self-paced learning program. Completing the repository exercises does not automatically provide an accredited certificate or professional qualification.

You can demonstrate your progress by maintaining a GitHub repository containing lab reports, screenshots, investigation notes, detection queries, and your capstone project. Only claim completion of exercises you have actually performed.

## 🤝 Support and Contributions

### 16. How do I get help if I'm stuck?

If you encounter a problem:

1. Review the relevant lab instructions and troubleshooting notes.
2. Check the official documentation for the tool you are using.
3. Open an issue in the [SOC Analyst Training Program repository](https://github.com/iftiurhossen11/soc-training-program) with a clear description of the problem.
4. Include relevant error messages, sanitized logs, and the steps needed to reproduce the issue.

**Important:** Never publish passwords, API keys, authentication tokens, personal information, or confidential organizational logs in a public issue.

### 17. Can I contribute to this repository?

Yes! Contributions that improve the learning experience are welcome.

You can contribute by:

- Correcting technical errors or improving documentation.
- Adding practical labs and safe, reproducible examples.
- Improving detection queries and troubleshooting instructions.
- Reporting broken links or unclear explanations.
- Suggesting additional learning resources.

Before submitting a pull request, read the repository's **Contributing Guidelines**, if available, and follow its instructions. If no contributing guide exists yet, open an issue to discuss a substantial proposed change before submitting it.

---

## 🎯 Final Note

The goal of this program is to build practical SOC Analyst skills through consistent study, hands-on exercises, careful investigation, and clear technical documentation.

**Learn the concepts. Practice safely. Verify your findings. Document your work.**
