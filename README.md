# *SOC Analyst 30-Day Challenge*

##🛡️***Hands-On Cybersecurity Challenge Portfolio: 30 Labs in 30 Days***

Welcome to my SOC Analyst 30-Day Challenge repository! This project showcases hands-on experience across six key SOC domains through daily lab exercises. Each lab demonstrates applied skills in threat detection, SIEM/EDR log analysis, incident response, packet capture review and the use of popular open-source tools.

## 📌 Domains Covered

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

Each lab folder contains detailed documentation, screenshots, and my personal reflections on the technical tasks performed.

---

## 📁 Repository Structure

The labs are grouped by topic, with each folder covering 5 days of hands-on activities.
SOC-Hands-On-Challenge/
├── 1-Log-Analysis/ # Days 01–05: Syslog parsing, SSH brute-force detection
├── 2-Network-Traffic-Analysis/ # Days 06–10: PCAPs, DNS, ARP spoofing (Wireshark)
├── 3-Incident-Response/ # Days 11–15: IR workflows, documentation, escalation
├── 4-Splunk/ # Days 16–20: Log correlation, threat detection
├── 5-Threat-Intel-Forensics/ # Days 21–25: WHOIS, VirusTotal, OSINT
├── 6-Wazuh-Endpoint-Detection/ # Days 26–30: Real-time detection rules, alerting
├── Screenshots/ # Annotated screenshots used across labs
├── .gitignore
├── LICENSE
└── README.md

Each **DAYXX** folder includes:
- `README.md` : Goals, tools used, analysis steps, alerts observerd, takeaways
- Referenced screenshots from `Screenshots/` 

## 🚀 Tools & Platforms Used

| Tool/Platform     | Purpose                                  |
|-------------------|------------------------------------------|
| **Splunk (Free)** | Log correlation and custom detection     |
| **Wireshark**     | Network traffic analysis via PCAP        |
| **Wazuh 4.10.1**  | SIEM/EDR deployment, rule tuning         |
| **Suricata**      | IDS integration and rule testing         |
| **VirusTotal**    | IOC enrichment and threat classification |
| **Kali Linux**    | Adversary simulation and forensics       |
| **CyberChef**     | Log decoding, hash conversion, etc.      |

## 🎯 Project Goals

- Demonstrate practical SOC analyst skills across a full detection/response lifecycle.
- Document learning for portfolio presentation and future reference.
- Prepare for cybersecurity roles requiring log analysis, SIEM/EDR tuning, and threat intel.

---

## 📈 Sample Outcomes

- ✅ Detected and triaged brute-force SSH attacks using Wazuh.
- ✅ Investigated real-world threat indicators using OSINT and Splunk.
- ✅ Parsed logs to identify privilege escalation attempts.
- ✅ Documented incident response playbooks and decision-making steps.
- ✅ Tuned detection rules and filtered out false positives.

---

## 📬 Connect With Me

📧 Questions or feedback?  
📎 [Connect with me on LinkedIn](https://linkedin.com/in/sunitanigam-sharma)

---

> _“Let’s detect threats, not just document them.”_ 🔍🔥
