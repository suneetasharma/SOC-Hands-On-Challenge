# Day 04 – Linux Log Analysis: Network-Based Detection Using UFW Firewall Logs

## 📌 Objective

Analyze Linux UFW (Uncomplicated Firewall) logs to detect unauthorized access attempts and blocked connections. Understand how log entries indicate firewall behavior, source IPs, and potential brute-force or scanning activity.

---

## 🛠️ Tools Used

- Ubuntu 20.04 LTS (VM)
- UFW (Uncomplicated Firewall)
- `/var/log/ufw.log`
- `grep`, `tail`, `less`, `awk`
- MITRE ATT&CK: [T1046 – Network Service Scanning](https://attack.mitre.org/techniques/T1046/)

---

## 🧪 Steps Performed

### ✅ Step 1: Verified and Enabled UFW

Checked status and enabled if inactive:
```bash
  - sudo ufw status
  - sudo ufw enable

- Allowed SSH only:
```bash
  - sudo ufw allow ssh

- Denied all other inbound traffic
```bash
  - sudo ufw default deny incoming


2. ✅ Step 2: Simulated Network Access Attempts

  - Used nmap and browser-based tools from another system or host

  - Simulated access to blocked ports (e.g., 21, 23, 3389)

  - Generated multiple UFW log entries

✅ Step 3: Analyzed UFW Log File

-  Viewed blocked attempts:

  - sudo tail -f /var/log/ufw.log

- Filtered logs by "BLOCK":

  - grep "BLOCK" /var/log/ufw.log


- Captured fields like:

  - SRC – Source IP address

  - DST – Destination IP

  - PROTO – Protocol

  - SPT/DPT – Source/Destination port

---

## 📸 Screenshot
<p align="center"> 
<img src="/Screenshots/Day04-UFW-Denied_v2.png" alt="UFW Blocked Log Screenshot" width="600"> 
</p>

---

## 🧠 Key Learnings
- UFW logs provide visibility into network denial events

- BLOCK IN entries help identify unauthorized scans or brute-force attempts

- Combining firewall logs with threat intel (e.g., AbuseIPDB) enhances incident context

---

## 🎯 Conclusion
- Firewall log monitoring is essential for identifying low-level reconnaissance and intrusion attempts. UFW provides accessible, log-rich alerts that serve as an early detection layer in SOC investigations.
