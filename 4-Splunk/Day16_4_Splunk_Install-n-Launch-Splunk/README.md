# 🛡️ Day 16 – Install and Configure Splunk

## 📌 Objective
The objective of this lab is to install and configure Splunk on an Ubuntu machine. and have Splunk up and running to collect and analyze security logs.

---

## 🛠️ Lab Setup

## Requirements
- System: Ubuntu Server 24-24.04.1 [ss-ubuntu - 192.168.70.4]
- Tools Required:
    - Splunk Enterprise (Free version for local setup)
    - Terminal (Command Line Access)


---

## 🧪 Steps to Install and Configure Splunk on Ubuntu

### Step 1: Download Splunk
1. Open Terminal and download Splunk using wget:
```
wget -O splunk-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb "https://download.splunk.com/products/splunk/releases/9.3.0/linux/splunk-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb" 
```

### 📸 Screenshot - Download Splunk
<p align="center">
  <img src="../../Screenshots/Day-16-Splunk_Download-Splunk.png" width="400">
</p> <p align="center"><em>Download Splunk</em></p>


2. Install Splunk
``` 
sudo dpkg -i splunk-ubuntu.deb
```

### 📸 Screenshot - Install Splunk
<p align="center">
  <img src="../../Screenshots/Day-16-Splunk_Install-Splunk.png" width="400">
</p> <p align="center"><em>Install Splunk</em></p>


### Step 2: Enable Splunk as a Service
1. Move to the splunk installation directory
```
cd /opt/splunk/bin
```

2. Accept the license agreement and enable Splunk at boot:
```
sudo ./splunk enable boot-start --accept-license
```

3. Start Splunk
```
sudo ./splunk start
```

### 📸 Screenshot - Start Splunk
<p align="center">
  <img src="../../Screenshots/Day-16-Splunk_Start-Splunk.png" width="400">
</p> <p align="center"><em>Start Splunk service</em></p>


4. When prompted, set up a admin username and password

### Step 3: Access Splunk Web Interface
1. Splunk install above can ONLY be accessible locally from http://127.0.0.1:8000. and can only be access via browser of your Linux desktop. So, to allow any user access Splunk globally, you have to bind the IP address to 0.0.0.0 in /opt/splunk/etc/splunk-launch.conf file. And allow port 8000 on tcp 
    - Blind IP address to 0.0.0.0 in splunk-launch.conf
    ```
    vi /opt/splunk/etc/splunk-launch.conf
    SPLUNK_BINDIP=0.0.0.0
    ```
    - Allow port 8000 on tcp
    ```
    sudo ufw allow 8000/tcp
    ```
    
    - Open a web browser and go to:
    ```
    http://192.168.70.4:8080
    ``` 

### 📸 Screenshot - Access Splunk Web Interface
<p align="center">
  <img src="../../Screenshots/Day-16-Splunk_Access-Splunk-Web-Interface.png" width="400">
</p> <p align="center"><em>Splunk Web Interface</em></p>



2. Log in with the admin credentials created above

### 📸 Screenshot - Splunk Admin Login
<p align="center">
  <img src="../../Screenshots/Day-16-Splunk_Admin-Login.png" width="400">
</p> <p align="center"><em>Splunk Admin Login</em></p>


---

## 🧠 Key Learnings
- Install and configure Splunk on an Ubuntu Linux server

---

## 🎯 Conclusion
✅ Successfully installed Splunk on an Ubuntu machine.
✅ Configured Splunk as a service and enabled auto-start.
