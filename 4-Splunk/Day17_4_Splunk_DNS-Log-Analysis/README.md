# 🛡️ Day 17 – [Lab Title Placeholder]

## 📌 Objective
In this lab, I learned 
- how to ingest and analyze DNS logs in Splunk. 
- Understand how to extract useful information such as DNS query types, source hosts, and common destinations.
- Practice building basic SPL (Search Processing Language) queries to investigate DNS activity.
---

## 🛠️ Lab Setup 
- ✅ Splunk: Already installed and accessible.
- ✅ Data Source: JSON-formatted Zeek DNS logs.
- 🌐 Uploaded sample Log File into Splunk for ingestion.

---

## 🧪 Steps to Upload DNS Log into Splunk
1. Go to Splunk Web → Settings > Add Data.
2. Choose Upload and select the file dns.log.
3. Set Source type: json or create a custom source type dns.
4. ex: Choose main or create a new index like dns_lab.
5. Finish the upload and confirm indexing.

---

## 🔍 Lab Tasks: Use SPL queries to perform following tasks:

✅Task 1: Identify the most frequently queried domain names
```
index=dns_lab sourcetype="json"
| stats count by query
| sort -count
```
 - - SPL Query to identify the most frequently queried domain names
  ```
  source="dns_logs.json" index="main" sourcetype="_json" | stats count by query | sort -count
  ```

## 📸 Screenshot - SPL Query - Most Frequently queried Domains
<p align="center">
  <img src="../../Screenshots/Day-17_Splunk_SPL-Most-Frequently-Queried-Domain-Name.png" width="400">
</p>


✅Task 2: Find the most active user IPs generating DNS traffic
```
index=dns_lab sourcetype="json"
| stats count by "id.orig_h"
| sort -count
```
  - SPL Query to find out the most active user IPs generating DNS traffic
  ```
  source="dns_logs.json" index="main" sourcetype="_json" | stats count by *id.orig_h* | sort -count
  ```

## 📸 Screenshot - SPL Query - Most Active User IPs generating DNS traffic
<p align="center">
  <img src="../../Screenshots/Day-17_Splunk_SPL-Most-Active-User-IPs-Generating-DNS-Traffic.png" width="400">
</p>


✅Task 3: Breakdown of DNS query types (A, AAAA, CNAME, PTR)
``` 
index=dns_lab sourcetype="json"
| stats count by qtype
```
  - SPL Query
  ```
  source="dns_logs.json" index="main" sourcetype="_json" | stats count by *id.orig_h* | sort -count
  ```

## 📸 Screenshot - SPL Breakdown of DNS Query Types
<p align="center">
  <img src="../../Screenshots/Day-17_Splunk_SPL-Breakdown-of-DNS-Query-Types.png" width="400">
</p>

---

## 🧠 Key Learnings
- Learned how to ingest logs files into Splunk
- And analyzed data using SPL (Search Processing Language) queries from the uploaded DNA logs file to extract valuable information on DNS query types, source hosts, and common destinations.

---

## 🎯 Conclusion
Splunk centralize logs collection from diverse system, applications and network devices into a single platform. This unified approach help SOC Analyst's visibility  across the entire IT environment, enabling security teams to detect threats and anomalies that might go unnoticed in siloed or fragmented log setups. With all logs in one place, organizations can implement consistent security controls, such as role-based access and tamper-evident storage, which help protect log integrity and prevent unauthorized access or manipulation. Centralized logging also supports real-time monitoring and automated alerting, allowing for faster detection and response to security incidents. Additionally, it simplifies forensic investigations and compliance reporting by providing a single, reliable source of truth for all security-relevant events. Overall, centralized log collection is foundational for proactive, efficient, and robust security monitoring.
