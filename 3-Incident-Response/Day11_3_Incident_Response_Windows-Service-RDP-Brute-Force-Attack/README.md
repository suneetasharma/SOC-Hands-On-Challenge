# 🛡️ Day 11 – Incident Response - Windows RDP Brute Force Detection

## 📌 Objective
Learn how to detect and respond to brute-force attacks against a Windows system using the built-in Event Viewer, and apply core principles from the NIST Incident Response lifecycle to take action as a SOC analyst.

## 🗂️ Table of Contents
- [What is Incident Response?](#what-is-incident-response)
- [Incident Response Lifecycle (NIST)](#incident-response-lifecycle-nist)
- [💥 Common Windows Security Incidents](#common-windows-security-incidents)
- [🧪 Lab Task: Simulate and Detect RDP Brute Force](#lab-task-simulate-and-detect-rdp-brute-force)
- [🚨 Attack Simulation (on Kali Linux)](#attack-simulation-on-kali-linux)
- [👁️ Detection via Event Viewer](#detection-via-event-viewer)
- [🛡️ Response Steps](#response-steps)
- [🧠 Key Learnings](#key-learnings)
- [📁 Evidence Collected](#evidence-collected)

---

## 🧠 What is Incident Response?
**Incident Response (IR)** is the structured process used by security teams to detect, contain, investigate, and recover from cybersecurity incidents like intrusion or malware attacks. 

---

## 🔄 Incident Response Lifecycle (NIST)

| **Phase**              | **Description**                |
|--------------------------------------|-----------------------------------------|
| Preparation     | Set up policies, logging, tools, and team readiness          |
| Detection and Analysis   | Monitor logs and alerts to identify abnormal activity |
| Containment, Eradication, Recovery | Isolate threat, clean environment, and restore operations |
| Post-Incident Activity   | Conduct root cause analysis and improve incident handling process |

---



<details>
<summary>💥 Common Windows Security Incidents</summary>

| **Incident Type**                    | **Description**              |
|-------------------------------------|-------------------------------|
| Unauthorized Login Attempts   | Brute-force or repeated failed login attempts |
| PowerShell-Based Attacks    | Obfuscated PowerShell used for exploitation   |
| Malware / Ransomware Execution  | Execution of malicious payloads or encryption software  |
| Credential Dumping    | Credential harvesting from memory (e.g., Mimikatz)   |
| Lateral Movement   | Using WMI/RDP to pivot across the network  |

</details>

----


## 🧪 Lab Task: Simulate and Detect RDP Brute Force

### 🖥️ Lab Setup

- **Target**: Windows Server 2022 (RDP Enabled) - [WIN2022SERVER - 192.168.70.8]
- **Attacker**: Kali Linux with Hydra [ss-Kali - 192.168.70.5]
- **Network**: Both machines connected to same virtual network
- **Tools**: Event Viewer, Windows Firewall, Nmap

### ✅ Preparation (on Windows Server)

1. Enable **RDP** in System Properties.

2. Allow **Remote Desktop** through Firewall.

3. Create a test user:
   ```powershell
   net user attackerlab Password123 /add 
   ```

4. Open Event Viewer and filter:
- Log: Windows Logs -> Security
- Filter by Event ID: **4625**


### 🚨Attack Simulation (on Kali Linux)

Ensure Hydra is installed 
``` 
sudo apt update && sudo apt install hydra
````

Run brute-force
```
sudo hydra -t 4 -V -f -l attackerlab -P /usr/share/wordlists/rockyou.txt rdp://192.168.70.8
```

5. Monitor resulting login failures on Windows

## 📸Screenshot - Attack Simulation from Kali

<p align="center">
  <img src="../../Screenshots/Day11-Incident-Response_Attack-Simulation-from-Kali-Linux.png" alt="Screenshot Placeholder" width="500">
</p>
<p align="center"><em>Hydra brute-force attack against RDP</em></p>



### 👁️ Detection via Event Viewer
- Event ID: 4625
- Logon Type: 10 (RDP/RemoteInteractive)
- Failure Reason: Unknown username or bad password
- Caller IP: 192.168.70.5 (IP of Kali Attacker)

##📸Screenshot - Detection via Event Viewer
<p align="center">
  <img src="../../Screenshots/Day11-Incident-Response_Detection-via-Event-Viewer.png" width="500">
</p>
<p align="center"><em>Multiple 4625 Failed Logons Detected</em></p>

---


## 🛡️ Response Steps

1. Correlate Events: Multiple 4625 failures from one IP

2. Block Attacker IP:
```
 New-NetFirewallRule -DisplayName "Block Attacker" -Direction Inbound -RemoteAddress 192.168.70.5 -Action Block
```

3. Validate Rule via Windows Firewall and re-run Hydra

4. Check Logs to confirm traffic is dropped

##📸Screenshot - Firewall Rules (Windows Server), Blocked rule confirmation (on Kali-Linux), MS Windows Firewall logs

<p align="center">
  <img src="../../Screenshots/Day11-Incident Response_Response-Steps-FW-rules_Drop-Logs.png" alt="Screenshot Placeholder" width="500">
</p>
<p align="center"><em>Firewall Rule created to block attacker IP</em></p>

---

## 🧠 Key Learnings
- ✅ Simulated a brute-force RDP attack using Hydra

- ✅ Monitored and filtered login failures via Event Viewer (Event ID 4625)

- ✅ Used New-NetFirewallRule to block the attacker's IP

- ✅ Understood the importance of correlation and containment in IR

- ✅ Practiced core steps from NIST's Incident Response Framework

---

### 📁 Evidence Collected
- ✔️ Hydra output from Kali Linux

- ✔️ Event Viewer screenshots showing repeated failures

- ✔️ Firewall rule screenshot confirming IP block