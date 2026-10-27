# Threat Hunting Report Template

## 📋 1. Hunt Details
- **Hunt ID:** [e.g., HUNT-2026-001]
- **Date:** [YYYY-MM-DD]
- **Analyst:** Md Iftiur Hossen Riyad
- **Hypothesis:** [e.g., "Attackers are using PowerShell to download payloads without dropping files on disk."]

## 🎯 2. Objective
*What is the goal of this hunt? (e.g., Validate hypothesis, find hidden threats).*

## 🔍 3. Hunt Methodology
- **Data Sources:** [Splunk, Sysmon, Firewall Logs, DNS Logs]
- **Search Queries (SPL):** 
  ```spl
  index=main EventCode=1 Image="*powershell.exe"
