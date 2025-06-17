# 🏢 Enterprise Cyber Range: Adversarial Simulation & Response

A virtualized cybersecurity lab that simulates a real-world enterprise environment to perform red team (adversarial simulation) and blue team (defensive monitoring) operations. Built using open-source tools like VirtualBox, Wazuh, Security Onion, and Kali Linux, this project enables hands-on learning of attack paths, detection mechanisms, and incident response strategies.

---

## 🎯 Objective

To design and deploy a simulated enterprise network that mimics core business infrastructure, and to carry out adversarial attack simulations alongside monitoring and response activities using modern cybersecurity tooling.

---

## 🧰 Infrastructure Overview

- **Hypervisor:** VirtualBox  
- **Network:** NAT Network (`project-x-nat`)  
- **Domain:** `corp.project-x-dc.com`  
- **Logging/Monitoring:** Wazuh, Sysmon, Winlogbeat, Security Onion  
- **Adversary Simulation:** Kali Linux (with tools like Nmap, Evil-WinRM, Impacket, Metasploit)

---

## 💻 Virtual Machines

| VM Name                 | OS                      | Role                                 |
|-------------------------|--------------------------|--------------------------------------|
| project-x-dc            | Windows Server 2025      | Domain Controller (AD, DNS, DHCP)    |
| project-x-win-client    | Windows 11 Enterprise    | User Workstation (RDP target)        |
| project-x-linux-client  | Ubuntu 22.04 Desktop     | Developer Workstation                |
| project-x-sec-box       | Ubuntu 22.04 Desktop     | Wazuh Manager + SIEM                 |
| project-x-sec-work      | Security Onion           | Network Security Monitoring (NIDS)   |
| project-x-email-svr     | Ubuntu Server 22.04      | Internal Email (Postfix SMTP)        |
| project-x-attacker      | Kali Linux 2024.2        | Attacker Machine (Red Team)          |

---

## 🔐 User Accounts

| Username / Email                      | Host                   | Role                        |
|---------------------------------------|------------------------|-----------------------------|
| Administrator                         | project-x-dc           | Domain Admin                |
| chitraksh@corp.project-x-dc.com       | project-x-win-client   | Standard Business User      |
| siddhant@linux-client                 | project-x-linux-client | Developer / Technical User  |
| project-x-sec-work                    | project-x-sec-work     | SOC Analyst                 |
| sec-work@sec-box                      | project-x-sec-box      | Security Engineer           |
| email-svr@project-x-email-svr         | project-x-email-svr    | Mail Server Admin           |
| attacker@attacker                     | project-x-attacker     | Red Team Operator / Attacker |

> 🔑 Passwords and internal policy files available in the report (not published here).

---

## 🔧 Key Tools

### 🛡️ Defensive Stack
- **Wazuh:** Host-based SIEM for log collection, rule-based alerting, and incident response.
- **Security Onion:** Network security monitoring using Zeek, Suricata, and Elastic Stack.
- **Sysmon + Winlogbeat:** High-fidelity endpoint telemetry and log forwarding to Wazuh.
- **Postfix:** Internal mail server to simulate phishing/spam scenarios.

### ⚔️ Offensive Tools
- **Kali Linux:** Offensive OS used for all attacks and simulations.
- **Nmap:** Network discovery and scanning.
- **Metasploit:** Exploitation framework for CVEs and post-exploitation.
- **Evil-WinRM:** Remote shell access to compromised Windows hosts.
- **Impacket:** AD exploitation tools like Pass-the-Hash, Kerberoasting.
- **Responder:** Credential theft via LLMNR poisoning and spoofed services.

---

## 🧪 Adversarial Simulation Flow

1. **Initial Access:** Phishing or exposed service exploitation.
2. **Privilege Escalation:** Local admin privilege abuse.
3. **Lateral Movement:** SMB, RDP, WinRM to pivot between machines.
4. **Credential Dumping:** Via Impacket or Mimikatz.
5. **Exfiltration:** Using encoded commands or direct transfers.

---

## 📊 Detection & Response

- Wazuh agents and Security Onion sensors monitor host and network activity.
- Alerts generated for:
  - Brute force and failed logins
  - Port scans and unusual network traffic
  - Execution of suspicious tools
- Dashboards in Wazuh and Kibana provide visibility into timelines and threat maps.

---

## 📄 Project Report

👉 ([Click here to access the full project report](https://github.com/sid42337/Enterprise_Cyber-Range/tree/main/Report))

---

## 🙌 Acknowledgements

Built as a college-level cybersecurity project to simulate real-world infrastructure, threats, and detection capabilities using only open-source tools.

---

