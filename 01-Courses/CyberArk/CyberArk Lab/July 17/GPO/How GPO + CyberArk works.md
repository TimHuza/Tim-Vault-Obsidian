#cyberark-labs 


![Image](https://images.openai.com/static-rsc-4/XmJaQesO6DdOU-djJrt7PXYTl548IEollQnuWkqdEo2MD9bB8n6FacdedC21CX5tixB6QW0UZ7OQVZoUJ_iKI5hyX46GyFqNgX3oRtipMU5jtGpua_-XQe05wzFeNbn6l2Zti0Lnsuwb5SfRPIR-MC4LbAO8D7qjbBzXH3UlPiVsZuZ31-P2HQEbUmHBck5w?purpose=fullsize)

Imagine a company is like a **big school**:

- **Active Directory (AD)** = the school's student database
    
- **GPO** = the school's rules
    
- **CyberArk** = the school's safe where important keys are stored
    

GPO and CyberArk work together to protect **powerful accounts** (privileged accounts).

---

# First: What problem are we trying to solve?

In a company there are special accounts:

Examples:

```
Administrator
Domain Admin
Server Admin
Database Admin
Service Accounts
```

These accounts are very powerful.

If an attacker steals:

```
Administrator
Password123
```

they can control many computers.

This is why companies use:

```
CyberArk + GPO
```

---

# The Big Picture

A company environment looks like this:

```
                 Active Directory
                       |
                       |
              +--------+--------+
              |                 |
             GPO            CyberArk
              |                 |
              |                 |
        Windows Servers     Password Vault
              |                 |
              |                 |
              +--------+--------+
                       |
                       |
              Protected Accounts
```

---

# Part 1: What does GPO do?

GPO controls the **rules**.

Example:

The company creates a GPO:

```
GPO Name:
CyberArk Security Policy
```

Inside:

```
Rules:
------------------

1. Disable local Administrator account

2. Allow RDP only from CyberArk PSM

3. Enable security auditing

4. Enforce password rules

5. Block dangerous settings
```

The servers receive these rules automatically.

---

# Part 2: What does CyberArk do?

CyberArk protects the **passwords**.

Without CyberArk:

```
Admin
 |
 |
 v
Server

Password:
Admin123
```

The password might be:

- written in a document
    
- shared in Teams
    
- stored in Excel
    
- known by many people
    

Very dangerous.

---

With CyberArk:

```
Admin
 |
 |
 v
CyberArk Vault

Password:
************
```

Nobody knows the real password.

CyberArk stores it safely.

---

# Now: How do GPO + CyberArk work together?

Let's follow a real example.

---

# Example: A Windows Server

Company has:

```
SERVER01

Local Administrator account:

Username:
Administrator

Password:
Secret123
```

Problem:

Who knows this password?

Maybe:

- IT team
    
- Developers
    
- Old employees
    

Bad.

---

## Step 1: GPO prepares the server

The company creates a GPO:

```
GPO:
"Prepare Server for CyberArk"
```

It applies:

```
Allow RDP from PSM servers only

Enable auditing

Configure security settings
```

Result:

```
SERVER01

RDP allowed:
     |
     |
     +---- CyberArk PSM only
```

---

## Step 2: CyberArk takes control

CyberArk discovers:

```
SERVER01\Administrator
```

It puts it into the Vault.

Now:

```
Administrator password

Before:

People know it

After:

CyberArk knows it
```

---

## Step 3: User wants administrator access

A user says:

"I need admin access to SERVER01"

Before CyberArk:

```
User
 |
 |
 v

SERVER01

Username: Administrator
Password: Secret123
```

The user sees the password.

❌ Bad.

---

With CyberArk:

```
User
 |
 |
 v
CyberArk

Request Access

 |
 |
 v

PSM

 |
 |
 v

SERVER01
```

The user never sees:

```
Administrator password
```

---

# Step 4: CyberArk changes the password

This is called:

## Automatic Password Management (APM)

CyberArk says:

"Time to change the password."

Example:

Before:

```
Administrator

Password:
Secret123
```

CyberArk changes it:

```
Administrator

Password:
A8#k92Lm!
```

Then updates the Vault.

Nobody needs to know.

---

# Where does GPO help here?

GPO makes sure Windows follows the security rules.

Example:

CyberArk says:

"Only PSM should connect."

GPO enforces:

```
Windows Firewall:
Allow:

PSM Server ✅

Everyone else ❌
```

---

# Another Example: Domain Admin

Imagine:

```
Domain Admin
```

This account can control the whole company.

Very dangerous.

CyberArk:

```
Stores password
Changes password
Records sessions
Controls access
```

GPO:

```
Controls where and how
Domain Admin can log in
```

Together:

```
             Domain Admin

                  |
                  |
             CyberArk Vault
                  |
                  |
              CyberArk PSM
                  |
                  |
              Windows Servers

                  +
                  
                 GPO
      (Security rules around everything)
```

---

# The easiest way to remember:

## GPO = The Police Rules 🚓

GPO says:

> "These are the rules everyone must follow."

Examples:

- Who can log in
    
- What settings are allowed
    
- What security controls exist
    

## CyberArk = The Bank Vault 🔐

CyberArk says:

> "These important passwords are locked here."

Examples:

- Admin passwords
    
- Service account passwords
    
- Root passwords
    

---

# In one sentence:

**GPO controls the Windows environment, while CyberArk protects and manages the powerful passwords inside that environment.**

They work together like this:

```
GPO
 |
 |-- Creates a secure Windows environment
 |
 v

Windows Servers
 |
 |
CyberArk
 |
 |-- Protects administrator accounts
 |-- Rotates passwords
 |-- Controls access
 |-- Records sessions
```

For a CyberArk beginner, this is the main idea you need to understand. 🔐