#journal 


### **1. CyberArk**
Today I viewed a video on **Backup and Restore**

I also did a **quiz** first time on 5/10 then 9/10
![[09-Journal/Attachements/August 21/backup-and-restore-quiz.png]]

---
### **2. Cyber Security**
Today I completed the lessons **51. Privileged Access Management** and **52. Security Controls** in **Identity & Access Management** section

#### 51. Privileged Access Management
#### 1. What is Privileged Access?

A **privileged account** is any account that has far more power and permissions than a normal, everyday user account. Think of normal accounts like regular employees who can only enter their own offices, while privileged accounts hold the "master keys" to the entire building.

#### 2. Why are Privileged Accounts Dangerous?

Because they hold the "keys to the kingdom," privileged accounts are the **absolute highest-value targets** for hackers. If an attacker compromises a normal user's account, they can usually only see that user's files. But if they steal an administrator's credentials, they can:

#### 3. Major Risks to Watch Out For

*   **Privileged Creep:** This is directly related to the "role creep" we discussed in access control. It happens when an employee slowly accumulates more and more permissions over time as they change jobs or help with projects, but their old, powerful administrative permissions are never removed.

*   **Shared Accounts:** This is when multiple employees use the same administrator login (like sharing one "Admin" username and password). This is a massive security failure because it destroys **accountability**; if a file is deleted, it is impossible to know which person actually did it. Every admin must have their own unique account.

*   **Poor Password Hygiene:** Using weak, reused, or factory-default passwords on accounts that control entire systems.

*   **Inactive Accounts:** When an employee leaves the company, but their powerful privileged account is left active. If a hacker finds this unused, unmonitored account, they can use it to slip into the system completely unnoticed.

#### 4. Enter PAM (The Guard for the Master Keys)

**Privileged Access Management (PAM)** is a specific security approach (combining tools and rules) designed to protect, control, and closely monitor these powerful admin accounts.

*   **Who** is trying to get privileged access?

*   **What** specific system are they trying to touch?

*   **When** are they doing it?

*   **How long** do they actually need to use it?

*   **What did they do** while they had that power?

#### 5. The Four Core Superpowers of a PAM System

1.  🔐 **Credential Vaulting**

2.  🎥 **Session Recording**

3.  ⏱️ **Just-in-Time (JIT) Access**

4.  🔄 **Password Rotation**

#### Study Guide Quick-Recall Cheatsheet

|Risk|The PAM Best Practice / Fix|Why it helps|
|:--|:--|:--|
|**Privileged Creep**|Apply **Least Privilege** & remove old accounts|Users only get the minimum access they need to do their job.|
|**Shared Accounts**|Eliminate them; use unique accounts|Ensures every single action can be traced back to a specific person.|
|**Poor Passwords**|Use **Credential Vaulting** & **MFA**|Passwords are hidden in a vault and require extra security verification to use.|
|**Always-On Power**|Use **Just-in-Time (JIT) Access**|Restricts the window of opportunity for an attacker if an account is compromised.|

![[privileged-access-management-infographic.png]]

I also did a quiz on 10/10
![[privileged-access-management-quiz.png]]

#### 52. Security Controls

For your study notes, here is a detailed, beginner-friendly breakdown of **Security Controls**.

In cybersecurity, we don't just throw technology at problems. We use a structured system of "guards" called **security controls** to keep systems safe.

---

#### 1. What is a Security Control?

A **security control** is any safeguard or countermeasure designed to protect an organization's systems and digital assets. Think of security controls as the safety features on a car (like seatbelts, airbags, and speed limits)—they are put in place to prevent accidents, minimize damage, and guide how things should run safely.

Every security control is put in place to support one of the core pillars of security, known as the **CIA Triad** and **Non-repudiation**:

- **Confidentiality:** Making sure only authorized people can access sensitive information. _(Example: A password protects your bank account so strangers can't see your balance)._
- **Integrity:** Ensuring that information remains accurate, complete, and is not improperly changed or tampered with. _(Example: Preventing a hacker from altering the amount of money on a digital check)._
- **Availability:** Ensuring that systems, networks, and data are up and running whenever authorized users need them. _(Example: Making sure a hospital's patient database doesn't crash during an emergency)._
- **Non-repudiation:** Ensuring that actions or transactions can be legally proven and cannot easily be denied by the person who did them. _(Example: Having a digital receipt or a system log that proves a specific employee authorized a financial transfer, preventing them from saying "it wasn't me")._

---

#### 2. The Three Security Control Categories
#### 💻 Category 1: Technical Security Controls

Technical controls are protections implemented directly through **technology, software, or computer systems**. They are also commonly referred to as **logical controls**.

- **How to remember it:** **Technical = Technology**. If a computer chip, a line of code, or a software program is doing the work, it is a technical control.
- **Examples of Technical Controls:**
    - **Firewalls:** Digital walls that monitor and filter incoming and outgoing network traffic to block hackers.
    - **Anti-malware software:** Programs (like antivirus) that scan, detect, and destroy malicious code on your computer.
    - **Operating system access controls:** Features like username and password prompts that restrict who can log into a computer.

#### 👮 Category 2: Operational Security Controls

Operational controls are security measures executed primarily by **people and day-to-day processes**, rather than computer code or software programs. These controls focus on human behavior and physical actions.

- **How to remember it:** **Operational = People + Processes**. If the security measure relies on a human being following a rule, performing a task, or standing guard, it is operational.
- **Examples of Operational Controls:**
    - **Security guards:** Physical personnel placed at doors to verify badges and prevent unauthorized visitors from entering a building.
    - **Security awareness training:** Education programs that teach employees how to spot phishing emails and avoid common social engineering scams.
    - **Training programs:** Teaching IT staff the correct step-by-step processes for setting up new hardware securely.

#### 📋 Category 3: Managerial Security Controls

Managerial controls provide the **oversight, administrative direction, and guidelines** for an organization's overall information security. They do not directly block hackers or guard doors; instead, they define the rules, identify risks, and decide how security should be run.

- **How to remember it:** **Managerial = Management + Oversight**. These are the high-level plans, legal documents, and decision-making processes created by company leadership.
- **Examples of Managerial Controls:**
    - **Risk identification:** Sitting down to analyze the business and identify where the biggest security weaknesses are.
    - **Security policies:** The official written rulebook of the company (e.g., a document stating: _"All employees must use Multi-Factor Authentication"_).
    - **Security management processes:** The strategic plans that dictate how the company will respond to a breach or audit.

#### Study Guide Quick-Recall Table

|Control Category|Who or What Does the Work?|Practical Examples|Memory Trick|
|:--|:--|:--|:--|
|**Technical**|**Technology and Systems**|Firewalls, anti-malware, system login screens|💻 Technology protects you.|
|**Operational**|**People and Processes**|Physical security guards, employee security training|👮 People and processes protect you.|
|**Managerial**|**Management and Oversight**|Security policy documents, risk assessments|📋 Management decides the rules.|

![[security-controls-infographic.png]]

I also did a quiz on 8/10
![[security-controls-quiz.png]]

---

### **3. Django**

