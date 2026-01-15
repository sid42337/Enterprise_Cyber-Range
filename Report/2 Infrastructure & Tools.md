# 2. Infrastructure & Tools

---

This section provides an in-depth overview of the technical components that power the cyber range. It includes the virtualization setup, operating systems, security tools used for both attack and defense, and utility software that supports the environment.

---

### 💻 Virtualization Environment

**Platform:** Oracle VirtualBox 7.1.8

**Type:** Local Virtualization

**Network Mode:** NAT Network (`Project-X-NAT`)

All virtual machines in this project were hosted using VirtualBox, which is a widely-used and free virtualization solution. The NAT Network mode allowed VMs to communicate internally while being isolated from the internet, which is important for safe experimentation.

You only needed to create a single NAT network (`Project-X-NAT`) with an IP range of `10.0.0.0/24`. All virtual machines used either static or dynamic IP addresses from this range.

This setup simulates an enterprise-like internal network while keeping it secure and manageable on a college-grade system.

---

### 💽 Operating Systems Used

| **VM Name** | **OS Version** |
| --- | --- |
| `project-x-dc` | Windows Server 2025 |
| `project-x-win-client` | Windows 11 Enterprise |
| `project-x-linux-client` | Ubuntu 22.04 Desktop |
| `project-x-sec-work` | Ubuntu 22.04 Desktop |
| `project-x-sec-box` | Security Onion 2.4 |
| `project-x-corp-svr` | Ubuntu Server 22.04 |
| `project-x-attacker` | Kali Linux 2024.2 |

---

### 🛠️ Tools

**Enterprise Tools + Defense**

1. **Microsoft Active Directory**: A directory service used for managing and organizing network resources, users, and permissions in a Windows environment.
2. **Wazuh**: An open-source security monitoring platform that provides intrusion detection, log analysis, vulnerability detection, and compliance reporting.
3. **MailHog**: MailHog is a lightweight email testing tool that acts as a fake SMTP server. It captures all outgoing emails sent by applications, without delivering them to real inboxes. You can inspect emails via a web interface or API.

**Offense**

1. **Evil-WinRM**: A powerful Ruby-based Windows Remote Management (WinRM) client used by penetration testers to connect to and interact with Windows systems, often for post exploitation tasks such as command execution and data extraction.
2. **Hydra**: A fast and flexible password-cracking tool designed to perform brute-force and dictionary-based attacks on various network protocols, including SSH, HTTP, FTP, and more.
3. **SecLists**: A comprehensive collection of penetration testing resources, including wordlists for usernames, passwords, web directories, and other payloads used in reconnaissance and exploitation phases.
4. **NetExec**: A network exploitation tool that enables remote command execution on target machines through various protocols, assisting in lateral movement and privilege escalation scenarios.
5. **XFreeRDP**: An open-source implementation of the Remote Desktop Protocol (RDP), enabling penetration testers to connect to and control Windows systems remotely for reconnaissance and post-exploitation purposes.
