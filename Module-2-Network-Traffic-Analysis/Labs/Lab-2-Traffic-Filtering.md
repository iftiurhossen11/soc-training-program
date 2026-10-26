# Lab 2: Capturing and Filtering Live Network Traffic

## 🎯 Objective
To capture live network traffic and use Wireshark's Display Filters to isolate specific protocols (DNS and HTTP). This is a core skill for SOC analysts to reduce noise and focus on relevant security events during incident response.

## 🛠️ Tools & Environment Used
- **Operating System:** Kali Linux VM
- **Tool:** Wireshark
- **Filtering Language:** Wireshark Display Filters

## 📝 Detailed Lab Steps & Execution

### Step 1: Filtering DNS Traffic
1. Started a live packet capture on the `eth0` interface.
2. Generated DNS traffic by executing `ping -c 4 google.com` in the terminal.
3. Applied the display filter: `dns`.
4. Observed the DNS queries (Standard query) and responses, confirming that the filter successfully isolated domain resolution traffic.

### Step 2: Filtering HTTP Traffic
1. Stopped the previous capture and started a new one.
2. Generated HTTP traffic by visiting an unencrypted website (e.g., `http://neverssl.com`) in the browser.
3. Applied the display filter: `http`.
4. Isolated HTTP GET requests and observed the plain-text data in the packet details.

## 📸 Screenshots & Evidence

**Screenshot 1: DNS Traffic Filtering**
*This shows Wireshark successfully filtering only DNS packets using the `dns` display filter.*
![DNS Filter](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab4-dns-filter.png)

**Screenshot 2: HTTP Traffic Filtering**
*This shows Wireshark filtering only HTTP packets using the `http` display filter.*
![HTTP Filter](https://raw.githubusercontent.com/iftiurhossen11/soc-training-program/main/Module-2-Network-Traffic-Analysis/Labs/lab4-http-filter.png)

## ✅ Conclusion
Successfully applied display filters to isolate DNS and HTTP traffic from a noisy network capture. This skill is essential for network forensics, allowing analysts to quickly focus on suspicious protocols during an investigation.
