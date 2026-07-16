#cyberark 

Think of a company network like a **large office building**:

- **Vertical movement = going UP to get more power (higher privileges)**
    
- **Lateral movement = moving SIDEWAYS to reach more systems**
    

They are both important concepts in **CyberArk**, because CyberArk is designed to protect privileged accounts that attackers try to steal and abuse during these movements.

---

# 1. What is Vertical Movement?

## Simple definition

**Vertical movement (also called privilege escalation)** is when an attacker tries to gain **higher permissions or privileges** on the same system.

The attacker moves **up the privilege ladder**.

Example:

```
Normal User
     |
     |
     ↓
Administrator
     |
     |
     ↓
Domain Admin
     |
     |
     ↓
Enterprise Admin
```

The attacker starts with a low-level account and tries to become a powerful administrator.

---

## Real-world example

Imagine you work in a company:

You have:

```
Employee Account
Username: tim.employee
Permission:
- Read emails
- Access your files
- Use company apps
```

An attacker steals your password.

They now have:

```
tim.employee
```

But they want more.

They try to become:

```
Administrator
```

because an administrator can:

- Install software
    
- Change security settings
    
- Create users
    
- Access other machines
    

This is **vertical movement**.

---

## How attackers perform vertical movement

Common methods:

### 1. Stealing privileged credentials

Example:

Attacker finds:

```
Administrator
Password: Admin123
```

Now they move upward:

```
User Account
      |
      ↓
Administrator Account
```

---

### 2. Exploiting vulnerabilities

Example:

A normal user has access to a vulnerable application.

The attacker exploits it:

```
Normal User
      |
      |
      ↓
System Administrator
```

---

### 3. Abusing misconfigured permissions

Example:

A user accidentally has:

```
Permission:
Run services as Administrator
```

The attacker abuses this.

---

# CyberArk and Vertical Movement

CyberArk protects against vertical movement by controlling **privileged accounts**.

Example:

Without CyberArk:

```
Administrator
Password:
Winter2026!
```

Many people know the password.

An attacker steals it.

---

With CyberArk:

```
Administrator Account

        |
        |
        ↓

CyberArk Vault
        |
        |
        ↓

Password is hidden
Password changes automatically
Access is monitored
```

The attacker cannot easily move upward.

---

# 2. What is Lateral Movement?

## Simple definition

**Lateral movement** is when an attacker moves from one compromised machine/account to another machine in the same environment.

They move **sideways**.

Example:

```
Computer A
     |
     |
     ↓
Computer B
     |
     |
     ↓
Database Server
     |
     |
     ↓
File Server
```

The attacker is exploring the network.

---

# Real-world example

Imagine a company has:

```
Employee Laptop
        |
        |
        ↓
File Server
        |
        |
        ↓
Database Server
        |
        |
        ↓
Domain Controller
```

The attacker first compromises:

```
Employee Laptop
```

But the valuable data is on:

```
Database Server
```

So they move:

```
Employee Laptop
        |
        |
        ↓
File Server
        |
        |
        ↓
Database Server
```

This is **lateral movement**.

---

# How attackers perform lateral movement

## 1. Using stolen credentials

Example:

They steal:

```
Username:
backup_admin

Password:
Password123
```

They try those credentials everywhere:

```
Laptop
 ✔

File Server
 ✔

Database Server
 ✔
```

---

## 2. Pass-the-Hash attack

Windows stores password hashes.

Instead of knowing the password:

```
Password:
Summer2026!
```

the attacker steals:

```
Hash:
A94A8FE5CC...
```

They use the hash to authenticate.

---

## 3. Remote services

Attackers may use:

- Remote Desktop (RDP)
    
- SSH
    
- PowerShell Remoting
    
- Windows Admin Shares
    

Example:

```
Attacker
    |
    |
    ↓
RDP
    |
    |
    ↓
Server
```

---

# CyberArk and Lateral Movement

CyberArk helps stop lateral movement because attackers often need **privileged credentials** to move around.

Example:

Without CyberArk:

```
Administrator password:

AdminPassword123
```

Used on:

```
Server 1
Server 2
Server 3
Server 4
```

If stolen:

Attacker controls everything.

---

With CyberArk:

```
Server 1 Admin Account
        |
        ↓
CyberArk Vault
        |
        ↓
Password automatically rotated

Server 2 Admin Account
        |
        ↓
CyberArk Vault
        |
        ↓
Different password
```

Even if one credential is compromised, movement is limited.

---

# Main Difference Between Vertical and Lateral Movement

||Vertical Movement|Lateral Movement|
|---|---|---|
|Direction|Up|Sideways|
|Goal|Gain more privileges|Reach more systems|
|Also called|Privilege Escalation|Network Movement|
|Example|User → Admin|PC → Server|
|Attacker wants|More power|More access|
|CyberArk protects|Privileged accounts|Credential abuse|

---

# Easy way to remember

Imagine a video game:

## Vertical Movement

You level up:

```
Level 1 Player
       |
       ↓
Level 50 Admin
```

You become stronger.

---

## Lateral Movement

You explore the map:

```
Town
 |
 ↓
Castle
 |
 ↓
Enemy Base
```

You reach new places.

---

# In a CyberArk attack scenario

A typical attack looks like this:

```
1. Initial Access
        |
        ↓
2. Attacker compromises employee account
        |
        ↓
3. Vertical Movement
   Become Administrator
        |
        ↓
4. Lateral Movement
   Move across servers
        |
        ↓
5. Access sensitive data
```

CyberArk's mission is mainly to make steps **3 and 4 much harder** by protecting privileged credentials and controlling privileged access.

A good beginner mental model:

> **Vertical movement = "How do I become more powerful?"**  
> **Lateral movement = "How do I reach more machines?"**