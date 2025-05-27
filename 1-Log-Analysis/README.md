# 1 Log Analysis
# 🧪 Day 01 - Log Analysis: Introduction to Logs and PowerShell Event Monitoring

#📌 Objective
To demonstrate how logs from different systems can be collected, analyzed, and used for security monitoring. This lab focuses on generating basic logs on both Windows and Linux systems and shows how SOC Analysts use logs to detect security incidents.
---
# 📖 What is a Log?
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
# 🔬 Lab Task: Simulating and Detecting Windows PowerShell Events

# 🖥️ Lab Setup

# ✅ Requirements:
- **Operating Systems**: Windows 10/11 or Windows Server 2019/2022, Linux (Ubuntu or CentOS)
- **Tools**:
  - Windows Event Viewer
  - PowerShell (pre-installed on Windows)
---
# 🛠️ Preparation
## On Windows:
1. **Open Group Policy Editor (`gpedit.msc`)**:
   - Navigate to:  
     `Computer Configuration > Administrative Templates > Windows Components > Windows PowerShell`
   - Enable:
     - Module Logging
     - Script Block Logging
     - Script Execution
2. **Open Event Viewer**:
   - Navigate to:  
     `Applications and Services Logs → Microsoft → Windows → PowerShell → Operational`
---
## 🧪 Step-by-Step Execution
### ✅ Step 1: Simulate a Suspicious PowerShell Command
Open PowerShell as Administrator and run:
  ``` powershell - Get-LocalUser | Select-Object Name, Enabled ```
  
This command lists all local user accounts on the system, whcih could be used by attackers to enumerate users post-exploitation.

### ✅ Step 2: Detect the Log in Event Viewer
  - Press ```Win + R ```, type ```eventvwr.msc```, and hit Enter
  - Navigate to: ```Applications and Services Logs → Microsoft → Windows → PowerShell → Operational ```
  - Click Filter Current Log, and filter for Event ID: 4104 (PowerShell script execution)
  - Locate the log showing the execution of the Get-LocalUser command
Screenshot:

🧠 Key Takeaways
- Enabled detailed PowerShell logging via Group Policy
- Simulated a potentially suspicious PowerShell command
- Identified and reviewed the event log (Event ID 4104) in Windows Event Viewer

🎯 Conclusion
- Understanding Log Analysis: Logs are a critical tool for detecting, investigating, and responding to security incidents.
- SOC Analyst Role: SOC Analysts depend heavily on logs to detect threats, trace activity, and maintain compliance.
- Practical Insight: Hands-on log generation and detection reinforce key skills for SOC roles.
