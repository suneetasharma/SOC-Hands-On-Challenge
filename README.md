# *SOC Analyst 30-Day Challenge*

##🛡️***SOC Analyst Hands-On Challenge Portfolio (30-Day Lab Series)***

Welcome to my SOC Analyst 30-Day Challenge Portfolio! This repository showcases hands-on cybersecurity skills developed through 30 lab exercises across 6 core SOC domains (daily labs focused on). Each lab focused on practical skills in threat detection, SIEM/EDR log analysis, incident response, and the use of open-source tools widely used by security operations centers:
- 📝 Log Analysis
- 🌐 Network Traffic & Packet Analysis (Wireshark)
- 🚨 Incident Response
- 📊 Splunk Investigations
- 🕵️ Threat Intelligence
- 🔍 Digital Forensics
- 🛠️ Wazuh Setup, Monitoring, and Alerting


## 🎯 Objectives

- Analyze and triage real-world security alerts using Wazuh and Suricata.
- Conduct packet analysis with Wireshark to uncover suspicious activity.
- Use Splunk for log correlation and alert investigation.
- Build and fine-tune detection rules.
- Simulate incident response processes with mapped MITRE ATT&CK techniques.

## 🛠️ Tools & Platforms

- **SIEM & EDR**: Wazuh, Suricata, CrowdStrike (simulated)
- **Log & Packet Analysis**: Splunk (trial), Wireshark
- **Threat Intel & Frameworks**: MITRE ATT&CK, Cyber Kill Chain
- **Scripting**: Python (log parsing and alert automation)

## 📚 Lab Themes

| Section             | Labs Covered     | Skills Highlighted                                      |
|---------------------|------------------|----------------------------------------------------------|
| Log Analysis        | Day 01–05        | Syslog parsing, alert review, SSH brute-force detection |
| Wireshark Basics    | Day 06–10        | PCAP analysis, DNS, ARP spoofing                        |
| Threat Intelligence | Day 11–15        | WHOIS, VirusTotal, IOC mapping                         |
| Wazuh & EDR         | Day 16–20        | Real-time detection rules, FIM, anomaly alerting        |
| Incident Response   | Day 21–25        | Playbook steps, triage documentation, escalation        |
| Splunk Scenarios    | Day 26–30        | Splunk search queries, log correlation, alert tuning    |

## 📈 Summary of Outcomes

- Created detection rules to identify brute-force SSH attempts and privilege escalation.
- Used MITRE ATT&CK mapping to correlate attacker behavior across different alerts.
- Documented investigation steps in triage reports.
- Learned how to distinguish false positives and validate true threats in lab data.

## 👀 Preview

Each lab includes:
- 🔍 Step-by-step screenshots or terminal outputs
- 📝 Written summaries of observations
- ⚠️ Notable alerts or detection insights
- ✅ Reflection on what was learned

Explore each section to follow my progression through real-world SOC tasks.

---

## 📁 Repository Structure

The labs are grouped by topic, with each folder covering 5 days of hands-on activities.
SOC-Hands-On-Challenge/
├── Log_Analysis/ # Day 01–05: Log analysis fundamentals
│ ├── Day01_Log_Basics/
│ ├── Day02_Windows_EventLogs/
│ ├── ...
├── Wireshark_Basics/ # Day 06–10: Network traffic analysis with Wireshark
├── Threat_Intelligence/ # Day 11–15: IOC Hunting, OSINT, etc.
├── Screenshots/ # Central folder for annotated screenshots
├── .gitignore
└── README.md

Each day folder includes:
- `README.md` documenting tools used, objectives, steps, and observations.
- Screenshots referenced inline from the central `Screenshots/` folder.

## 🚀 Tools Used

- Splunk (Free Edition)
- Wireshark
- Wazuh 4.10.1 (on Ubuntu server)
- Suricata
- VirusTotal / AbuseIPDB / URLScan.io
- Kali Linux
- CyberChef

## 🎯 Goal

This portfolio is built to:
- Demonstrate my SOC skillset and lab experience.
- Serve as a knowledge base for others.
- Support job interviews and career growth in cybersecurity.

## 📬 Contact
If you'd like to connect or ask about a specific lab, feel free to [reach out via LinkedIn](https://linkedin.com/in/sunitanigam-sharma).
---
Let’s detect threats, not just document them. 🔍🔥
