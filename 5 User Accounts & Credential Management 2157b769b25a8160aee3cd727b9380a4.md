# 5. User Accounts & Credential Management

---

This section outlines the different user accounts created in the enterprise environment, their roles, and how authentication and credential policies were managed. These accounts help simulate a realistic business environment with varying levels of access and user activity.

### 🧑‍💼 **1. Account Roles**

A variety of accounts were created to represent common user types in an organization. Each account was associated with a specific host and had a unique role in the simulation.

| **Username / Email** | **Associated Host** | **Role** | **Password** |
| --- | --- | --- | --- |
| `Administrator` | project-x-dc | Domain Admin | `@Deeboodah1!` |
| `johnd@corp.project-x-dc.com` | project-x-win-client | Standard Business User | `@password123!` |
| `janed@linux-client` | project-x-linux-client | Developer / Technical User | `@password123!` |
| `project-x-sec-work` | project-x-sec-work | SOC Analyst | `@password123!` |
| `secuser@sec-box` | project-x-sec-box | Security Engineer | `@password123!` |
| `corp-svr@project-x-email-svr` | project-x-email-svr | Mail Server Admin | `@password123!` |
| `attacker@attacker` | project-x-attacker | Red Team Operator / Attacker | `attacker` |

---

### 🔐 **2. Password Policies**

For simplicity and control, all user passwords were predefined and manually set. This helped in focusing on attack simulation rather than unpredictable password management. The policy was intentionally lax to allow successful brute-force and credential attacks. 

- **Password Format:** Simple, human-readable passwords to simulate weak credentials.
- **Examples:**
    - `@Deeboodah1!` for Administrator
    - `@password123!` for standard users

> **Note:** Weak passwords were used intentionally to create realistic vulnerability scenarios (e.g., password reuse).
> 

---

### 🎛️ **3. Access Levels**

User access was divided based on job role and function to simulate real-world permissions:

- **Administrator:**
    - Full control over the domain and all resources.
    - Used for setting up AD, GPOs, and managing users.
- **Standard Users (Chitraksh / Siddhant):**
    - Local access to their own workstations.
    - Can be targeted for phishing, credential theft, or lateral movement.
- **Security Roles (sec-work / sec-box):**
    - Access to Wazuh, Security Onion, and internal log servers.
    - Used in detection, analysis, and response tasks.
- **Attacker:**
    - Starts outside the environment with no internal access.
    - Gains privileges through exploitation and lateral movement.

---

> Note: Account creation and permission assignment were done through the Domain Controller (project-x-dc) using standard Active Directory practices.
>