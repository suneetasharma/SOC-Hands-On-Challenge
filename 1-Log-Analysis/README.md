## Log Analysis

🧪 Day 01 - Log Analysis: Introduction to Logs and PowerShell Event Monitoring

## 📌*Objective:* 

To demonstrate how logs from different systems can be collected, analyzed, and used for security monitoring. This lab focuses on generating basic logs on both Windows and Linux systems and shows how SOC Analysts use logs to detect security incidents.

---

### 📖 What is a Log?

A **log** is a record of events in a system that captures important actions such as:

- 🕒 **Timestamp**
- 📝 **Event Description**
- ❗ **Severity** (Critical, Error, Warning, Information)
- 🔗 **Source** (User, Process, Service)
  
Logs are essential for:

- Understanding system behavior  
- Detecting security incidents  
- Conducting forensic investigations
  
---

🔬 *Lab Task*: **Simulating and Detecting Windows PowerShell Events**


## 🖥️ Lab Setup


## ✅ Requirements:

- **Operating Systems**: Windows 10/11 or Windows Server 2019/2022, Linux (Ubuntu or CentOS)
- **Tools**:
  - Windows Event Viewer
  - PowerShell (pre-installed on Windows)
    
---

### 🛠️ Preparation Steps:

### Enable PowerShell Logging via Group Policy:

1. **Open Group Policy Editor (`gpedit.msc`)**:
   - Navigate to:  
     `Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell`
     
   - Enable the following:
     
     - Module Logging
     - Script Block Logging
     - Script Execution
       
2. **Open Event Viewer**:
   - Navigate to:  
     `Applications and Services Logs → Microsoft → Windows → PowerShell → Operational`

💡 These settings allow visibility into what PowerShell commands are being executed—critical for detecting malicious activity.

---

## 🧪 Execution Steps

### ✅ Step 1: Simulate a Suspicious PowerShell Command

Open **PowerShell as Administrator** and run:

  `powershell 
    Get-LocalUser | Select-Object Name, Enabled `
  
This command lists all local user accounts on the system, whcih could be used by attackers to enumerate users post-exploitation.

### ✅ Step 2: Detect the Log in Event Viewer

  1. Press 'Win + R', type 'eventvwr.msc', and press Enter

  2. Navigate to:
      `Applications and Services Logs → Microsoft → Windows → PowerShell → Operational`

  3. Click *Filter Current Log*, and filter for `Event ID: 4104`

  4. Review the log showing the execution of the `Get-LocalUser` command

📸 PowerShell Event ID 4104 ![PowerShell Log - Event ID 4104](../Screenshots/Day01-EventID4104.png)


## 🧠*Key Learning Outcomes*

✅ Enabled advanced PowerShell logging through Group Policy

✅ Simulated user enumeration via PowerShell

✅ Located and analyzed script execution logs (Event ID 4104)


## 🎯*Conclusion*

- Understanding Logs: Logs provide critical visibility for detecting and investigating threats.
- SOC Analyst Relevance: Analysts depend on logs like PowerShell execution records to trace suspicious behavior.
- Hands-On Insight: This lab reinforces key detection skills used in real-world SOC environments.


