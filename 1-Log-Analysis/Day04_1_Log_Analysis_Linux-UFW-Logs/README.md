# Day 04 – UFW Log Analysis (Linux)

This lab demonstrates how logs from different systems can be collected, analyzed, and used for security monitoring. Specifically, this lab focuses on how to simulate and detect Linux UFW-denied connections and understand their significance in threat detection workflows.

## 🧪 Lab Objective
To understand how to generate UFW (Uncomplicated Firewall) log entries by simulating denied inbound traffic on a Linux system and to analyze those logs to detect potential security threats.

---
## 🛠️ Lab Setup – Requirements

**System**: Ubuntu 20.04 or similar  
**Tools**:
- UFW (pre-installed on Ubuntu)
- `/var/log/syslog` or `/var/log/ufw.log`
- Terminal (bash or zsh)

---

## 🧪 Steps to Simulate and Detect UFW Logs

### Step 1: Enable UFW and Logging

sudo ufw enable
sudo ufw logging on


Step 2: Create a Rule to Deny Specific Traffic

sudo ufw deny 8080

Step 3: Simulate Inbound Traffic to Port 8080
Use another system or tool (e.g., nmap or telnet) to connect:

sudo nmap -p80 -Pn 192.168.70.5

Step 4: Check UFW Logs
Look in /var/log/syslog or /var/log/ufw.log for entries similar to:

[UFW BLOCK] IN=enp0s3 OUT= MAC=... SRC=... DST=... PROTO=TCP SPT=... DPT=8080 ...

You can filter them with:

sudo grep 'UFW BLOCK' /var/log/syslog


## 📸 Screenshot

<p align="center">
  <img src="https://raw.githubusercontent.com/suneetasharma/SOC-Hands-On-Challenge/main/Screenshots/Day04-UFW-Denied_Compressed.png" alt="UFW Screenshot" width="600" />
</p>

---

🧠 Key Takeaways
- **UFW Logs** are critical for understanding inbound/outbound network activity.
- **SOC Analysts** often inspect UFW-denied entries to spot brute-force attempts, port scans, or misconfigurations.
- These logs can be ingested into SIEM platforms like Wazuh, Splunk, or ELK for real-time alerting.


✅ Conclusion
✅ Enabled and configured UFW logging on a Linux system

✅ Simulated a denied inbound connection using port 8080

✅ Identified and analyzed the UFW log entry in /var/log/syslog

✅ Interpreted critical fields like SRC, DPT, and PROTO for threat context

✅ Understood the importance of UFW logs in SOC environments for identifying unauthorized access attempts
