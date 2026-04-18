# 🚀 VLAN Network Design + FTP Server Deployment

This project demonstrates the design and implementation of a segmented network using VLANs combined with an FTP server deployed on Ubuntu.

  

---

## 📌 Project Overview

The goal of this project is to simulate a small enterprise network with:

* Network segmentation using VLANs
* Inter-VLAN routing (Router-on-a-Stick)
* FTP server deployment for file sharing
* Client-server communication across different VLANs

---

## 🏗️ Network Topology

* VLAN 10 → Users → `192.168.10.0/24`

* VLAN 20 → IT → `192.168.20.0/24`

* VLAN 100 → Servers → `192.168.100.0/24`

* Router handles inter-VLAN routing

* Switch configured with trunk and access ports

---

## ⚙️ Technologies Used

* Cisco IOS (Routing & Switching)
* Ubuntu Server
* vsftpd (FTP Server)
* Windows Client
* Networking concepts: VLAN, Trunking, Inter-VLAN Routing

---

## 🔧 Configuration Steps

### 1. VLAN Configuration (Switch)

* Create VLANs (10, 20, 100)
* Assign access ports
* Configure trunk link to router

---

### 2. Inter-VLAN Routing (Router)

* Configure sub-interfaces
* Assign gateway IPs:

  * `192.168.10.1`
  * `192.168.20.1`
  * `192.168.100.1`

---

### 3. FTP Server Setup (Ubuntu)

Install vsftpd:

```bash
sudo apt update
sudo apt install vsftpd -y
```

Enable service:

```bash
sudo systemctl start vsftpd
sudo systemctl enable vsftpd
```

---

### 4. FTP Configuration

Edit:

```bash
sudo nano /etc/vsftpd.conf
```

Key settings:

```ini
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES
allow_writeable_chroot=YES
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=40100
```

---

### 5. Firewall Configuration

```bash
sudo ufw allow 21/tcp
sudo ufw allow 40000:40100/tcp
```

---

### 6. Client Configuration

Example:

* IP: `192.168.10.5`
* Gateway: `192.168.10.1`

Connect using:

```bash
ftp 192.168.100.10
```

---

## 🧪 Testing

* Ping between VLANs ✅
* FTP connection successful ✅
* File upload/download working ✅

---

## ⚠️ Challenges

* Inter-VLAN communication troubleshooting
* Passive FTP port configuration
* File permission management

---

## 🎯 Key Learnings

* VLAN segmentation improves security and organization
* Router-on-a-Stick is a simple inter-VLAN solution
* Deploying real services enhances practical skills

---

## 📷 Screenshots

*Add your topology and test screenshots here*

---

## 🔮 Future Improvements

* Add DHCP Server
* Implement ACL for security
* Add monitoring (SNMP / Zabbix)

---

## 👨‍💻 Author

**Your Name**
