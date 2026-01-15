# 9. Adversary Simulation

---

### Cyber Attack Simulation Diagram

![image.png](image%20133.png)

---

## Cyber Attack Overview

We are going to simulate an end-to-end cyber-attack on ProjectX’s business network. The end goal is to capture sensitive files and achieve persistence inside the business network, so that we can log back in at our discretion.

Up until this point, we have built an enterprise or business network to “emulate” a real-world environment, something you would often see deployed to a much larger scale in the real-world.

---

### Threat Actor Motivations

Who we will impersonate? A hacker, also known as threat actors.

Threat actors (will use this interchangeably with attacker) have various motives. Most of what you see on the major news outlets and dedicated security news websites are financially motivated attackers, opportunistic in conducting their operations in hopes of financial gain or extortion.

Attackers can act alone, in a disparate community, using or helping others along the way, or in a selective group.

Outside of financial motives, attackers can align with different motives, a few the major ones are:

- Espionage: Nation-state actors may target governments, corporations, or organizations to gather intelligence, gain strategic advantages, or sabotage operations.
- Disruption: Hacktivists or adversaries may aim to disrupt services, systems, or operations to make a political or social statement or damage reputations.
- Revenge or Retaliation: Disgruntled employees or individuals may launch attacks to settle personal grievances or harm their targets.
- Ideological or Political Agendas: Cyberattacks may be motivated by an attempt to promote or enforce certain beliefs or ideologies, often tied to hacktivist movements.

---

### Cyber Attack Anatomy

Let’s overview the anatomy of a cyber-attack and review the major steps involved to achieve our objective.

Starting with the diagram below.

![](https://docs.projectsecurity.io/assets/images/e101/p11/4.png)

Each of these steps aims to achieve a specific outcome. To conduct a successful cyber-attack, its imperative attackers take the proactive steps from initial access to persistence.

These steps are leveraged in separate phases but are often chained together. For example, once an attacker gains initial access or lateral movement, they will perform additional reconnaissance on the network to see what is available.

Most often, attackers want to stay hidden in the network with unfettered access for as long as possible. Each of these steps brings the attacker closer to their end goal or motive.

These steps were first built by Lockheed Martin as a conceptual model to understand and defend against cyber-attacks, known as the Cyber Attack Kill Chain.

As the industry continued to mature its approach to proactive detection, the MITRE ATT&CK framework was built to expand these ideas by providing a real-world repository of tactics, techniques, and procedures (TTPs) used by threat actors, broken down into generalized steps attackers take to control a business or organization.

### **👀 Reconnaissance[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#reconnaissance)**

Also referred to as 'recon'. This is first phase of a cyber-attack where attackers gather information about their target to identify vulnerabilities they can exploit. This phase is all about preparation and involves collecting as much data as possible about the target's systems, network, employees, or infrastructure without triggering alarms.

### **🎯 Initial Access[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#initial-access)**

Attackers establish a foothold in the target’s environment. This is the entry point, achieved by exploiting vulnerabilities, phishing, using compromised credentials, or exploiting misconfigurations. The goal is to gain access to the target network while avoiding detection, setting the stage for further malicious activities.

### **👉 Lateral Movement[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#lateral-movement)**

Attackers navigate through a compromised network to access more systems, resources, or sensitive data. They move from the initial access point by exploiting vulnerabilities, using stolen credentials, and leveraging tools at their disposal. The aim is to expand control and find valuable assets without raising suspicion.

### **📈 Privilege Escalation[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#privilege-escalation)**

Attackers increase their level of access within the target environment. This is done by exploiting system vulnerabilities, misconfigurations, or weak permissions to move from a standard user to an admin or system-level account. It allows attackers to execute critical tasks and access sensitive data more freely.

### **🚀 Data Exfiltration[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#data-exfiltration)**

Attackers transfer stolen data out of the target environment. This may include sensitive files, credentials, or intellectual property. Attackers often disguise or encrypt the data to evade detection during the transfer process, using channels like email, file-sharing platforms, or compromised systems.

### **📩 Persistence[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#persistence)**

Attackers ensure ongoing access to the compromised system even after reboots or initial detection attempts. This involves creating backdoors, modifying system configurations, or installing malware that enables them to maintain control over the environment for extended periods.

### **❌ Defense Evasion[¶](https://docs.projectsecurity.io/e101/cyberattacksimulation/#defense-evasion)**

Attackers employ techniques to avoid detection and bypass security measures. This includes obfuscating malware, disabling security tools, using fileless attacks, or manipulating logs. The objective is to operate undetected, prolonging their access and reducing the chances of discovery.

---

### The Scenario

In this lab, we are going to “simulate” each step by leveraging techniques and tools at our disposal as an attacker. By leveraging default, insecure, and outdated configurations and software, our attacker wants to use their skills for their own personal gain. These configurations, although outdated and disabled by default, can still often be found in business networks to this day.

Our attacker is financially motivated, attempting to steal sensitive data. They have identified ProjectX as a target organization to conduct their operations so they can extort and steal some sensitive information, perhaps a username, password, and proprietary files.

🧠 Attacker Motive: **Financially Motivated**

🏆 Goal: **Exfiltrate Sensitive Data**