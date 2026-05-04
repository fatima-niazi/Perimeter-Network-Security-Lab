# 🔐 Perimeter Network Security Lab

**pfSense + Suricata IDS + Attack Simulation**

---

## 📌 Overview

This project demonstrates a complete **perimeter security implementation** in a virtual lab environment.
It integrates firewall enforcement, intrusion detection, Active Directory, and attack simulation to validate **defence in depth**.

---

## 🎯 Objectives

* Deploy **pfSense** as an edge firewall & gateway
* Configure **LAN firewall rules** to control traffic
* Implement **Suricata IDS** with custom detection rules
* Simulate real-world attacks from an attacker machine
* Verify security controls (AD, GPOs, VPN) remain intact

---

## 🖥️ Lab Environment

| Machine  | IP Address    | Role              |
| -------- | ------------- | ----------------- |
| pfSense  | 192.168.10.4  | Firewall & Router |
| DC01     | 192.168.10.10 | Domain Controller |
| ADMIN01  | 192.168.10.20 | Admin Workstation |
| CL01     | 192.168.10.30 | Client            |
| ATTACK01 | 192.168.10.40 | Attacker (Kali)   |
| VPN01    | 192.168.10.50 | VPN Server        |
| IDS01    | 192.168.10.60 | Suricata IDS      |

---

## 🌐 Network Architecture

* **LAN:** 192.168.10.0/24 (Internal network)
* **WAN:** NAT (Internet via VMware)
* **VPN:** 192.168.30.0/24

---

## 🔥 Firewall Configuration (pfSense)

* Block ICMP from client machine
* Block RDP access to Domain Controller
* Allow required Active Directory ports (DNS, Kerberos, LDAP, SMB)
* Allow VPN client access to LAN
* Enable logging on all rules

---

## 🛡️ IDS Configuration (Suricata)

Custom detection rules added for:

* SQL Injection
* Cross-Site Scripting (XSS)
* Brute Force attacks (RDP, SSH, SMB)
* LLMNR / NBT-NS poisoning

---

## ⚔️ Attack Simulation

Performed attacks from ATTACK01 to validate controls:

* 🔍 Network Reconnaissance (Nmap)
* 💣 SMBv1 / EternalBlue Check
* 🔐 Brute Force Attack (Hydra)
* 🧪 SQL Injection
* 🧪 XSS Injection
* 🎭 LLMNR Poisoning (Responder)
* 🔑 VPN Access Testing
* 🔒 TLS Version Verification

---

## 📊 Results

* Firewall successfully blocked restricted traffic
* Suricata detected malicious patterns in real time
* Account lockout policy stopped brute force attacks
* LLMNR poisoning failed due to GPO hardening
* SMBv1 disabled → EternalBlue not exploitable
* Only TLS 1.2 allowed (TLS 1.0/1.1 disabled)

---

## 📈 Monitoring & Logging

* pfSense firewall logs
* Suricata IDS alerts (`fast.log`)
* Sysmon logs on Domain Controller
* Windows Admin Center monitoring

---

## ⚠️ Issues & Fixes

* DNS misconfiguration on IDS → fixed `/etc/resolv.conf`
* VPN issues → installed & configured `xl2tpd`
* Suricata rules missing → manually created `local.rules`
* pfSense rules conflict → rebuilt clean rule set

---

## ✅ Conclusion

This lab demonstrates a practical implementation of:

* Network-level security enforcement
* Intrusion detection and monitoring
* Secure remote access via VPN
* Attack detection and prevention

It validates a **defence-in-depth strategy** across multiple security layers.

---

## 🔗 Author

**Bint e Fatima Niazi**

* LinkedIn: https://www.linkedin.com/in/bint-e-fatima-niazi/
* GitHub: https://github.com/fatima-niazi

---

⭐ If you found this useful, consider giving the repo a star!
