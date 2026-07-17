#cyberark-labs 

# What is GPO? (Simple Explanation)

**GPO = Group Policy Object**

A **GPO is a set of rules/settings that an administrator creates to control Windows computers and users in a company.**

Think of a school:

Imagine you are the principal of a school with 500 computers.

You want:

- Every computer to have the same security settings
    
- Students cannot install random software
    
- Screens lock after 10 minutes
    
- USB drives are blocked
    
- Passwords must be strong
    

Instead of going to every computer and changing settings manually...

You create **one rule book**.

That rule book is a **GPO**.

---

# Real World Example

Without GPO:

```
Computer 1:
    Password length = 8

Computer 2:
    Password length = 12

Computer 3:
    USB allowed

Computer 4:
    USB blocked
```

Very messy.

---

With GPO:

Administrator creates:

```
GPO: Company Security Policy

Rules:
-------------
Password minimum length: 14
Lock screen after: 15 minutes
Disable USB storage
Enable Firewall
```

Then Windows automatically applies it:

```
             Active Directory
                    |
                    |
        Company Security GPO
                    |
       ------------------------
       |          |           |
    PC-001     PC-002      PC-003
```

All computers follow the same rules.

---

# Where does GPO live?

GPO belongs to **Microsoft Active Directory (AD)**.

A typical company has:

```
Active Directory Domain
          |
          |
     Organizational Units (OU)
          |
          |
        Computers
          |
          |
          GPOs
```

Example:

```
Company.local

|
|--- Users
|
|--- Computers
|
|--- Servers
|
|--- Domain Controllers
```

Each part can have different GPOs.

---

# What is an OU?

Before understanding GPO, you need to know OU.

**OU = Organizational Unit**

It is like a folder where you organize computers and users.

Example:

```
Company.local

|
+--- Finance OU
|       |
|       +--- Finance-PC-01
|       +--- Finance-PC-02
|
+--- IT OU
|       |
|       +--- Admin-PC-01
|
+--- Servers OU
        |
        +--- Server01
        +--- Server02
```

Then you can say:

"Apply this GPO only to Finance computers."

---

# How does GPO work?

The process:

## Step 1: Administrator creates a GPO

Example:

```
GPO Name:

CyberArk Security Policy
```

Inside:

```
Password Policy:
    Minimum password length = 20

Security:
    Enable auditing

Windows:
    Disable local admin accounts
```

---

## Step 2: Administrator links GPO to something

A GPO does nothing by itself.

It needs to be attached to:

- Domain
    
- OU
    
- Site
    

Example:

```
CyberArk Servers OU

        |
        |
        v

CyberArk Security Policy GPO
```

Now every server inside that OU receives it.

---

## Step 3: Computer checks for GPO

Windows computers regularly ask Active Directory:

"Hey, do I have new rules?"

This process is called:

```
Group Policy Update
```

Command:

```
gpupdate /force
```

The computer downloads the policies.

---

## Step 4: Settings are applied

Example:

Before:

```
Administrator account:
Password never expires = YES
```

After GPO:

```
Password never expires = NO
```

The computer changes automatically.

---

# GPO Structure

A GPO has two main parts:

```
GPO
 |
 |---- Computer Configuration
 |
 |---- User Configuration
```

---

# 1. Computer Configuration

These settings affect the computer.

Example:

```
Computer Configuration

Security Settings
       |
       +--- Password Policy
       |
       +--- Firewall Rules
       |
       +--- Audit Policies
```

Example:

"All servers must enable firewall."

---

# 2. User Configuration

These settings affect users.

Example:

```
User Configuration

Policies
 |
 +--- Desktop settings
 |
 +--- Software restrictions
 |
 +--- Login scripts
```

Example:

"Employees cannot access Control Panel."

---

# Now the CyberArk Connection 🔐

This is where GPO becomes important.

CyberArk works with **Windows privileged accounts**.

Examples:

- Domain Admin accounts
    
- Local Administrator accounts
    
- Service accounts
    

Companies use GPO to control these accounts.

---

# Example: [[How GPO + CyberArk works|CyberArk + GPO]]

Imagine a company:

```
Active Directory

|
+--- Servers OU
        |
        |
        +--- Windows Server 01
        +--- Windows Server 02
        +--- Windows Server 03
```

CyberArk manages:

```
Administrator account
```

CyberArk wants:

```
Password changes every 7 days
```

But Windows must allow:

```
Password change
Remote login
Security policies
```

GPO helps configure the servers.

---

# Example: Disable Local Admin Accounts

A company does NOT want:

```
Administrator
Password123
```

on every server.

They create GPO:

```
GPO:
"Disable Local Admin"

Action:
Disable local Administrator account
```

Then CyberArk manages a separate account:

```
CyberArkAdmin
```

instead.

---

# Example: CyberArk PSM and GPO

Remember PSM?

```
User
 |
 |
 v
CyberArk PSM
 |
 |
 v
Target Server
```

GPO can control:

- Who can log in
    
- RDP settings
    
- Firewall rules
    
- Security settings
    

Example:

GPO:

```
Allow RDP login only from:

CyberArk PSM Servers
```

So:

Normal user:

```
User ----X----> Server
```

CyberArk:

```
User
 |
 v
PSM
 |
 v
Server

Allowed
```

---

# GPO Processing Order

When Windows receives multiple GPOs, there is an order.

The famous rule:

```
L S D O U
```

Means:

## L = Local

Computer's own policy.

↓

## S = Site

Active Directory site policy.

↓

## D = Domain

Company-wide policies.

↓

## O = Organizational Unit

Specific department policies.

---

Example:

```
Local GPO:

Password length = 8


Domain GPO:

Password length = 12


CyberArk OU GPO:

Password length = 20
```

Final result:

```
Password length = 20
```

because OU is applied last.

---

# Why do companies use GPO?

Because it gives:

✅ Central management  
✅ Security control  
✅ Consistent settings  
✅ Faster configuration  
✅ Less human mistakes

---

# GPO vs CyberArk (Very Important Difference)

Many beginners confuse them.

|GPO|CyberArk|
|---|---|
|Controls Windows settings|Protects privileged accounts|
|Part of Active Directory|PAM solution|
|Applies rules|Stores passwords securely|
|Manages computers/users|Manages admin credentials|
|Microsoft technology|Cybersecurity platform|

They work together.

---

# Simple Memory Trick 🧠

Think:

**GPO = The School Rules**

Example:

"The school says:

- wear uniform
    
- no phones
    
- lock doors"
    

Everyone follows.

**CyberArk = The School Safe**

Example:

"The safe protects:

- keys
    
- important documents
    
- passwords"
    

---

So:

```
GPO
 |
 |--- Controls the environment

CyberArk
 |
 |--- Protects the important passwords inside that environment
```

In a real company:

```
Active Directory
        |
        |
       GPO
        |
        |
 Windows Servers
        |
        |
    CyberArk protects
    Administrator accounts
```

That is how GPO fits into the CyberArk world. 🔐