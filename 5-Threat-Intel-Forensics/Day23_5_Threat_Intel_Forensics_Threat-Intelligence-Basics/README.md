# 🛡️ Day 23 – Threat Intelligence Basics

## 📌 Objective
 In this lab, I learned how to extract Indicators of Compromise (IOCs) from a suspicious email and use threat intelligence tools to investigate their context and maliciousness.

##  What is Threat Intelligence?
Threat Intelligence (TI) is information about threats, threat actors, and their tactics. It helps SOC analysts investigate alerts faster, make informed decisions, and respond to incidents more effectively.

## Types of Threat Intelligence:
Tactical: IOCs like IPs, hashes, domains
Operational: Info about campaigns, malware families
Strategic: Big-picture trends, threat groups, geopolitical context
---

## Lab Setup
-📩 Download Email Sample: sample-1.eml
- 💻 Tools You Will Use:
    - VirusTotal
    - AbuseIPDB
    - URLScan.io
    - AlienVault OTX
    - ThreatFox
    - MXToolbox Header Analyzer

---

## Tasks
- What is the type of the malicious file?
- What country is this IP registered in?
- What malware name (if any) is associated with this file on VirusTotal?

---

## Required Submission
- 🔹 IP Lookup - The IP address 185.220.101.19 belongs to a Tor network and has a self-signed certificate for anonymity

 ### Screenshot from AbuseIPDB showing details of 185.220.101.19
<p align="center">
  <img src="../../Screenshots/Day-23_Threat-Intelligence_IP-Lookup.png" alt="AbuseIPDB showing details of 185.220.101.19" width="500">
</p>

- 🔹 Domain Lookup - The domain name secure-login-verification.com is associated with phishing attacks. 

 ### Screenshot from VirusTotal showing details of secure-login-verification
<p align="center">
  <img src="../../Screenshots/Day-23_Threat-Intelligence_Domain-Lookup.png" alt="VirusTotal showing details of secure-login-verification" width="500">
</p>

- 🔹 Hash Analysis - The hash 44d88612fea8a8f36de82e1278abb02f is associated with the Eicar testing file and is not malicious. Screenshot from VirusTotal showing file type, detection ratio, and malware name for the hash 44d88612fea8a8f36de82e1278abb02f. It's merely used to trigger antivirus software detection mechanisms.

 ### Screenshot from VirusTotal showing details of Hash
<p align="center">
  <img src="../../Screenshots/Day-23_Threat-Intelligence_Hash-Analysis.png" alt="VirusTotal showing details of Hash" width="500">
</p>

-🔹 Threat Intelligence Feed (Optional Bonus) - The IOC found in AlienVault OTX or ThreatFox with campaign name or tags

 ### Screenshot from ThreatFox with compaign tags
<p align="center">
  <img src="../../Screenshots/Day-23_Threat-Intelligence_ThreatFox-with-TI-Compaign-Tags.png" alt="ThreatFox with Compaign tags" width="500">
</p>

## ✅ Learning Outcome
In this lab, I learned:
- How to extract IOCs from suspicious phishing emails
- And use Threat Intelligence tools to investigate their context and maliciousness, such as assess IPs, domains, and links
- Gain confidence in making escalation decisions based on threat intelligence
- Develop investigation habits like documentation and screenshot evidence

---


