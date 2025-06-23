# 🛡️ Day 13 – Detecting and Removing Malicious Cron Jobs - Linux 

## 📌 Objective
Investigate and respond to a malicious cron job used by an attacker to maintain persistence on a Linux system. And simulate the attack, detect the malicious scheduled task, analyze the script, and remove the threat — applying the full incident response lifecycle.

---

## 📘 What is a Cron Job?
A cron job is a scheduled task that runs automatically at defined intervals on Unix/Linux systems. Attackers often use cron to re-execute payloads, reconnect to command-and-control servers, or maintain access to a compromised system.

### 🛠️Key Features:
Run commands automatically (e.g., every minute, daily, weekly)
Useful for backups, updates, monitoring scripts, etc.
Works in the background via the cron service
🧾Format of a crontab entry:
*  *  *  *  *  command-to-run
│  │  │  │  │
│  │  │  │  └─ Day of the week (0-7, Sun = 0 or 7)
│  │  │  └──── Month (1 - 12)
│  │  └─────── Day of month (1 - 31)
│  └────────── Hour (0 - 23)
└───────────── Minute (0 - 59)


## 🔄 Incident Response Lifecycle (NIST)

| **Phase**                | **Description**     |
|--------------------------------------|------------------------------|
| Preparation | Ensure system logging is active and users are trained to detect unusual cron behavior. |
| Detection and Analysis | Identify unauthorized cron entries and investigate associated scripts or IP addresses.|
| Containment, Eradication, Recovery | Stop the malicious cron activity, remove the script, and restore system configuration. |
| Post-Incident Activity | Document the incident, and set alerts for future cron job changes. |


## 🛠️ ⚠️ Scenario: A Malicious Cron Job is Running Every Minute
An attacker has added a cron job that silently runs a malicious script from /tmp every minute. Your job is to detect it, understand its behavior, and remove it safely.

## 🛠️ Lab Setup

## System Requirements:
- Ubuntu 20.04 Kali Linux
- Terminal with sudo access

### Simulate the Incident:
1. Create a fake "malicious" script:
```
echo -e '#!/bin/bash\necho "Ping from attacker server" >> /tmp/.cron.log' > /tmp/malicious.sh
chmod +x /tmp/malicious.sh
```

2. Add a cron job for the current user:
```
echo "* * * * * /tmp/malicious.sh" >> /var/spool/cron/root
```

### 📸 Screenshot
<p align="center">
  <img src="../../Screenshots/Day-13-Incident-Response_Simulate-Incident-Malicious-Script.png" width="400">
</p> <p align="center"><em>Simulate Incident - Malicious Script</em></p>

---

## 🧪 Step-by-Step Investigation

### Step 1. Preparation
- Make sure cron is installed and running:
```
sudo systemctl status cron 
``` 
- Enable logging (cron logs are usually in /var/log/syslog or /var/log/cron).


### Step 2. Detection and Analysis
- Check for suspicious cron entries:
```
crontab -l
```

- Search cron directories for unauthorized jobs:
```
grep -r "/tmp/" /etc/cron* /var/spool/cron/crontabs
```

- Review logs to confirm execution:
```
cat /tmp/.cron.log
```

- Analyze the script:
```
cat /tmp/malicious.sh
```

### 📸 Screenshot
<p align="center">
  <img src="../../Screenshots/Day-13-Incident-Response_Investigation_Detection-and-Analysis.png" width="400">
</p> <p align="center"><em>Detection and Analysis</em></p>


### Step 3. Containment, Eradication, and Recovery
- Remove the malicious cron job:
``` crontab -l | grep -v "malicious.sh" | crontab -
```

 - Delete the script and its output:
 ```
rm -f /tmp/malicious.sh /tmp/.cron.log
```

- Restart the cron service: 
```
sudo systemctl restart cron
```

### Step 4. Post-Incident Activity
- Document the following:
- When the cron job was added
- What the script was doing
- Any signs of lateral movement or download activity

- Recommendations:
- Restrict cron job access to authorized users only
- Enable cron integrity checks
- Set up alerts for new cron entries (using auditd or inotify)

### 📸 Screenshot
<p align="center">
  <img src="../../Screenshots/Day-13-Incident-Response_Containment-Eradication-Recovery.png" width="400">
</p> <p align="center"><em>Hydra brute-force attack against RDP</em></p>

---

## 🧠 Key Learnings
- ✅ Simulate Cron Job Create a malicious script and schedule it via cron 
- ✅ Investigate Detect the cron job and examine the script behavior 
- ✅ Respond Remove the script and the cron entry 
- ✅ Document Record all findings and suggest prevention steps

---

## 🎯 Conclusion
- Learned to use the incident response process to respond to a suspicious malicious script on a linux machine.
- Monitor cron directories /var/spool/cron/crontab /etc/cron*
- Monitor logs /var/log/syslogs for executed cron jobs
- Contained, Eradicate the incident by deleting the cron entries and the malicious script.

---