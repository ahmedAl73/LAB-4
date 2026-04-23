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
The attack began with initial access to the OT web server (192.168.50.10) through the exploitation of the Shellshock vulnerability (CVE-2014-6271). The attacker, operating from the external IP address 203.0.113.100, sent a specially crafted HTTP request to a vulnerable CGI script hosted on the Apache web server. This request contained a malicious payload embedded in an HTTP header, which was processed by the Bash shell. Due to improper input handling, Bash executed the attacker’s command, granting remote code execution without authentication.

Once access was established, the attacker gained privileges equivalent to the web server process. This allowed them to execute system-level commands, access system files, and modify configurations. From this foothold, the attacker began exploring the internal OT network. Because of weak network segmentation and insufficient access controls, the attacker was able to move laterally from the compromised web server to SCADA devices using unauthorized SSH sessions. Internal trust relationships within the OT environment made it easier for the attacker to access additional systems without being blocked.

After gaining deeper access, the attacker initiated data exfiltration by transferring approximately 2.3 GB of sensitive data from the OT network to an external destination. This likely occurred through the compromised web server, which acted as a bridge between internal systems and the external network. The absence of effective monitoring and alerting systems allowed this activity to continue without immediate detection. Additionally, the attacker manipulated bash history files and Apache logs to conceal their actions, making forensic analysis more difficult.

The impact of this incident is significant, particularly in a critical infrastructure environment such as a water utility system. Unauthorized access to SCADA systems could allow attackers to manipulate water treatment processes, disrupt operations, or cause physical damage to infrastructure. This incident highlights the importance of proper patch management, strong network segmentation, and continuous monitoring to detect and prevent similar attacks in the future.

---

### TCP vs UDP Security Analysis
TCP and UDP are both transport layer protocols, but they differ significantly in terms of security and reliability. TCP is a connection-oriented protocol that uses a three-way handshake (SYN, SYN-ACK, ACK) to establish communication between devices. This process ensures that both the sender and receiver are synchronized before data transmission begins. Because TCP maintains connection state and uses acknowledgments, it provides better visibility for security tools such as firewalls and intrusion detection systems. Suspicious connections can be tracked, logged, and terminated more effectively.

In contrast, UDP is a connectionless protocol that does not establish a formal session before transmitting data. This lack of a handshake makes UDP faster and more efficient for real-time applications, but it also introduces security risks. Since UDP does not verify the identity of the sender, it is more vulnerable to spoofing attacks, where an attacker falsifies the source IP address. Additionally, the absence of connection tracking makes it more difficult for security systems to monitor and detect malicious activity.

Overall, TCP provides stronger security visibility and control due to its connection-oriented design, while UDP prioritizes speed and efficiency at the cost of reduced security monitoring and increased susceptibility to spoofing attacks.

---

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
