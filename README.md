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
The attack began with initial access to the OT web server (192.168.50.10) through the exploitation of the Shellshock vulnerability (CVE-2014-6271). The attacker, operating from the external IP address 203.0.113.100, sent a specially crafted HTTP request to a vulnerable CGI script hosted on the Apache web server. Due to improper input handling in the Bash shell, the malicious payload embedded within the HTTP header was executed by the server, granting the attacker remote code execution capabilities.
Once inside the system, the attacker gained the same privileges as the web server process, which allowed them to execute commands, access system files, and manipulate configurations. This level of access enabled the attacker to establish persistence and begin exploring the internal OT network. The lack of proper access controls and segmentation allowed the attacker to move laterally from the compromised web server to SCADA devices using unauthorized SSH sessions. Since trust relationships existed within the OT environment, the attacker was able to authenticate or bypass protections without significant resistance.
The attacker then initiated data exfiltration, transferring approximately 2.3 GB of sensitive data from the OT network to an external destination. This likely occurred through the same compromised server, which acted as a bridge between internal systems and the external network. Weak monitoring and insufficient logging controls contributed to the delay in detection. Additionally, the attacker manipulated bash history and Apache logs to hide their activity, making forensic analysis more difficult.
The impact of this attack is significant, particularly in a critical infrastructure environment such as a water utility system. Unauthorized access to SCADA systems could allow attackers to manipulate water treatment processes, disrupt service delivery, or cause physical damage to infrastructure. This incident highlights the importance of patch management, network segmentation, and continuous monitoring in protecting sensitive operational technology environments.
---

### TCP vs UDP Security AnalysisTCP vs UDP Security Analysis
TCP and UDP are both transport layer protocols, but they differ significantly in terms of security and reliability. TCP is a connection-oriented protocol that uses a three-way handshake (SYN, SYN-ACK, ACK) to establish communication between devices. This process ensures that both the sender and receiver are synchronized before data transmission begins. Because TCP maintains connection state and uses acknowledgments, it provides better visibility for security tools such as firewalls and intrusion detection systems. Suspicious connections can be tracked, logged, and terminated more effectively.
In contrast, UDP is a connectionless protocol that does not establish a formal session before transmitting data. This lack of a handshake makes UDP faster and more efficient for real-time applications, but it also introduces security risks. Since UDP does not verify the identity of the sender, it is more vulnerable to spoofing attacks, where an attacker falsifies the source IP address. Additionally, the absence of connection tracking makes it more difficult for security systems to monitor and detect malicious activity.
Overall, TCP provides stronger security visibility and control, while UDP prioritizes speed at the cost of reduced security monitoring capabilities.

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
---

## 📅 Date
March 2026
# LAB-4
