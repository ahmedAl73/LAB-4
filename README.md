# LAB-4: Enterprise LAN Security Assessment

## 📌 Overview
This project is part of IT 520 and focuses on designing, implementing, and securing an enterprise network for a simulated organization: Winslow Bay Municipal Utility District (WBMUD).

The lab demonstrates practical skills in network architecture, protocol security, vulnerability analysis, and incident response.

---

## 🎯 Objectives
- Apply OSI model concepts across network configurations
- Design a segmented enterprise network (IT, OT, Remote)
- Analyze security differences between protocols (TCP/UDP, HTTP/HTTPS, SSH)
- Simulate the Shellshock vulnerability (CVE-2014-6271)
- Perform incident response and attack path analysis
- Document findings in a professional format

---

## 🖧 Network Architecture
The network consists of three main segments:

- **IT Network** – Administrative systems  
- **OT Network** – SCADA and industrial control systems  
- **Remote Pump Station** – WAN-connected infrastructure  
- **DMZ** – Simulated attacker node  

---

## 🔐 Security Analysis
This lab includes analysis of:

- **Transport Layer (Layer 4):**
  - TCP vs UDP security trade-offs  

- **Application Layer (Layer 7):**
  - HTTP vs HTTPS (encryption and MITM protection)
  - SSH vs Telnet (secure remote access)

---

## ⚠️ Vulnerability Simulation
A simulated **Shellshock attack** was performed on a web server to demonstrate:

- Remote code execution via Bash
- Exploitation through CGI scripts
- Risks in unpatched systems

### 🛡️ Mitigation Strategies
- Patch management (update Bash)
- Web Application Firewall (WAF)
- Network segmentation

---

## 🚨 Incident Response
A simulated attack scenario was analyzed, including:

- Initial access via vulnerable web server
- Lateral movement to SCADA devices
- Data exfiltration
- Log manipulation

### 🔍 Key Actions
- Attack path reconstruction  
- Root cause analysis  
- Multi-layer remediation plan  

---

## 📁 Repository Contents
---

## 🧠 Key Takeaways
- Network segmentation is critical for protecting OT systems  
- Encryption (HTTPS, SSH) is essential in modern networks  
- Unpatched vulnerabilities can lead to full system compromise  
- Incident response requires both technical and strategic planning  

---

## 👨‍💻 Author
Ahmed Alkhawlani  
IT 520 – Network Security  

---

## 📅 Date
March 2026
# LAB-4
