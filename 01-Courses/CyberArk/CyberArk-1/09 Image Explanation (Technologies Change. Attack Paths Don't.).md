#cyberark 

![[09-technologies-change-attack-paths-dont.png|409]]
This image explains a **cybersecurity idea called "attack paths"** and how **CyberArk helps stop attackers from moving through an organization after they gain access**.

The main message:

> **"Technologies Change. Attack Paths Don't."**

means:

- Computers, cloud services, applications, and tools keep changing.
    
- But attackers usually follow the same pattern:
    
    1. Get an initial foothold.
        
    2. Steal credentials.
        
    3. Move around the network.
        
    4. Gain higher privileges.
        
    5. Reach critical systems.
        

CyberArk focuses on stopping this chain.

Let's go step-by-step.

---

# 1. Understand the "attack path"

Imagine a company as a building.

- Employees = people with keys.
    
- Servers = important rooms.
    
- Admin accounts = master keys.
    
- Passwords = keys.
    

An attacker wants to go from:

```
Outside the building
        |
        ↓
Employee computer
        |
        ↓
Admin account
        |
        ↓
Important server
        |
        ↓
Company control
```

This journey is called an:

## Attack Path

An attack path is the **route an attacker takes to reach valuable resources**.

---

# 2. The people and systems on the left side

Look at the left side:

```
External Attacker
       |
       |
Remote Vendor
IT Admin
Business User
Developer
Robot
Application
Internal Attacker
```

These represent possible starting points.

An attacker can enter through many places.

---

## A) External Attacker

This is someone outside the company.

Example:

A hacker on the internet.

Possible attacks:

- Phishing email
    
- Stolen password
    
- Exploiting a vulnerability
    

Example:

```
Hacker
  |
  |
Stolen employee password
  |
  |
Employee account
```

---

## B) Business User

Normal employees.

Example:

A marketing employee.

They usually have:

- Email access
    
- Documents
    
- Business applications
    

But maybe not:

- Server administrator access
    

---

## C) IT Admin

This is very important.

IT administrators have powerful accounts.

Example:

```
Normal User:
Can open Word documents

IT Admin:
Can create users
Can install software
Can change servers
```

If an attacker steals an IT admin account:

The damage can be huge.

---

## D) Developer

Developers may have access to:

- Source code
    
- Databases
    
- Cloud systems
    

Example:

A developer accidentally exposes:

```
database_password = "Admin123"
```

An attacker can use it.

---

## E) Robot / Application

Modern companies have machines doing work.

Examples:

- Automation scripts
    
- Bots
    
- Service accounts
    

These also have credentials.

---

# 3. The first red wall: PREVENT CREDENTIAL THEFT

The image says:

> PREVENT CREDENTIAL THEFT

This is the first defense.

The attacker wants:

```
Username + Password
```

because credentials are like keys.

Example:

Attacker steals:

```
Administrator
Password123
```

Now they can log in.

CyberArk protects credentials by:

- Storing passwords in a secure vault
    
- Rotating passwords automatically
    
- Removing exposed credentials
    
- Controlling who can access passwords
    

---

## Without CyberArk:

```
Admin password

    ↓

Stored in:
- Excel file
- Sticky note
- Shared document

    ↓

Attacker steals it
```

---

## With CyberArk:

```
Admin password

        ↓

CyberArk Vault

        ↓

User requests access

        ↓

CyberArk checks permission

        ↓

Temporary access granted
```

---

# 4. The attacker enters the environment

Look at the red arrow.

The attacker has passed the first barrier.

Example:

```
External attacker

        ↓

Employee computer

        ↓

Network access
```

The attacker is now inside.

This is called:

## Initial Access

The attacker has a foothold.

---

# 5. Lateral Movement

The image says:

> STOP [[Lateral & Vertical Movements|LATERAL & VERTICAL MOVEMENT]]

This is one of the most important concepts.

---

## Lateral Movement = moving sideways

Imagine a company network:

```
Computer A      Computer B      Server C
    |               |              |
    --------------------------------
```

An attacker gets into Computer A.

They move:

```
Computer A
     |
     ↓
Computer B
     |
     ↓
Database Server
```

This is lateral movement.

They are exploring.

---

Example:

A hacker compromises:

```
John's laptop
```

Then finds:

```
Admin account saved on laptop
```

Then moves to:

```
Domain Controller
```

Now they control the company.

---

# 6. Vertical Movement (Privilege Escalation)

Vertical movement means:

## Becoming more powerful

Example:

Starting:

```
Regular User
```

Then:

```
Administrator
```

Then:

```
Domain Admin
```

Like leveling up in a game.

---

Example:

```
Employee Account

      ↓

IT Admin Account

      ↓

Domain Administrator

      ↓

Complete control
```

The image calls this:

> PRIVILEGE ESCALATION & ABUSE

---

# 7. The red walls represent security boundaries

The image shows multiple red walls.

These are security barriers.

Think of them as doors:

```
Outside
  |
[Door 1]
  |
Employee Network
  |
[Door 2]
  |
Server Network
  |
[Door 3]
  |
Critical Systems
```

CyberArk tries to make sure attackers cannot simply walk through every door.

---

# 8. The attacker reaches the "internal attacker" area

The middle shows:

```
Internal Attacker
```

This means:

The attacker is no longer outside.

They are inside the environment.

They may have:

- Stolen credentials
    
- Compromised accounts
    
- Admin privileges
    

Now they can attack internally.

---

# 9. The final target: critical systems

The top-right area represents important systems.

Examples:

- Production servers
    
- Databases
    
- Cloud infrastructure
    
- Security systems
    

The attacker wants:

```
Access
  |
Control
  |
Damage
```

Possible outcomes:

- Steal data
    
- Delete files
    
- Encrypt systems (ransomware)
    
- Spy on company operations
    

---

# 10. Where CyberArk fits in

CyberArk is a:

## Privileged Access Management (PAM) solution

PAM means:

> Controlling and protecting powerful accounts.

The most dangerous accounts are:

- Administrator accounts
    
- Root accounts
    
- Service accounts
    
- Cloud admin accounts
    

---

CyberArk helps by:

## 1. Vaulting passwords

Instead of storing:

```
Admin password:
Winter2026!
```

somewhere unsafe:

```
CyberArk Vault
        |
        |
Encrypted storage
```

---

## 2. Password rotation

Example:

Before:

```
Admin123
```

After:

```
x7K9!pQ2@
```

Automatically changed.

---

## 3. Just-In-Time Access (JIT)

Instead of:

```
Admin access forever
```

you get:

```
Admin access

for 30 minutes

then removed
```

---

## 4. Session monitoring

CyberArk can record privileged sessions.

Example:

```
Admin logs into server

        ↓

CyberArk records actions

        ↓

Audit trail created
```

---

# The whole attack story (simple version)

Here is what the image is showing:

```
1. Hacker starts outside
        |
        ↓
2. Steals credentials
        |
        ↓
3. Enters company network
        |
        ↓
4. Moves sideways
        |
        ↓
5. Finds admin accounts
        |
        ↓
6. Escalates privileges
        |
        ↓
7. Reaches critical systems
```

CyberArk tries to break this chain:

```
Prevent stealing credentials
          ↓
Limit privilege
          ↓
Stop movement
          ↓
Protect critical systems
```

---

# Beginner summary

This image is basically saying:

> "Attackers do not usually hack directly into the most important server. They start somewhere small, steal credentials, move through the company, gain more power, and eventually reach valuable systems. CyberArk protects the powerful accounts and blocks this journey."

The most important CyberArk concepts to remember:

|Concept|Meaning|
|---|---|
|Credential Theft|Stealing usernames/passwords|
|Privileged Account|Powerful account like admin/root|
|PAM|Managing and protecting powerful accounts|
|Lateral Movement|Moving between systems|
|Privilege Escalation|Becoming more powerful|
|Vault|Secure storage for credentials|
|JIT Access|Temporary privileged access|

For a CyberArk beginner, **understanding this attack path is the foundation**, because almost every CyberArk product is designed to break one of these steps.