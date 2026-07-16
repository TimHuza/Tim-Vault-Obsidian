#concepts 

## What is an RDP file?

**RDP file** stands for **Remote Desktop Protocol file**.

Simply put:

> An RDP file is a small configuration file that tells your computer **how to connect to another computer using Remote Desktop**.

It usually has the extension:

```
filename.rdp
```

Inside the file, it contains settings like:

- Which computer to connect to
    
- Which username to use
    
- Screen resolution
    
- Display settings
    
- Security settings
    
- Connection options
    

Example:

```
full address:s:192.168.1.50
username:s:Administrator
screen mode id:i:2
desktopwidth:i:1920
desktopheight:i:1080
```

This means:

- Connect to computer `192.168.1.50`
    
- Use username `Administrator`
    
- Open a full-screen session
    

---

# What is RDP itself?

Before understanding the file, you need to understand **RDP**.

**RDP (Remote Desktop Protocol)** is a Microsoft protocol that allows you to control another Windows computer remotely.

Example:

You have:

```
Your laptop
     |
     | RDP connection
     |
     ↓
Windows Server
```

You see the server's desktop on your screen and can:

- Open programs
    
- Run commands
    
- Install software
    
- Manage files
    

It is like sitting in front of the server physically.

---

# Real-life example without CyberArk

Imagine a company has a Windows server:

```
Server01
IP: 10.10.10.20
```

An administrator wants to connect.

Instead of typing everything manually:

1. Open Remote Desktop Connection
    
2. Enter:
    

```
Computer: 10.10.10.20
Username: Admin
```

3. Click Connect
    

Windows can save these settings into:

```
Server01.rdp
```

Next time:

Double-click:

```
Server01.rdp
```

and it automatically opens the connection.

---

# Why is RDP important in CyberArk?

In CyberArk, RDP is one of the most common ways administrators access privileged machines.

Normally, without CyberArk:

```
Admin
 |
 | RDP
 |
 ↓
Production Server

Password:
Admin123!
```

Problem:

The admin knows the privileged password.

If the account is compromised:

```
Attacker
 |
 | steals password
 |
 ↓
Production Server
```

Huge security risk.

---

# How CyberArk changes this

With CyberArk PSM:

```
Admin
 |
 | clicks RDP connection
 |
 ↓
CyberArk PSM Server
 |
 | uses stored password
 |
 ↓
Target Server
```

The admin **does not know the password**.

CyberArk:

1. Retrieves the password from the Vault
    
2. Logs into the target server
    
3. Opens an RDP session
    
4. Records the session
    
5. Monitors activity
    

---

# What happens with a CyberArk RDP file?

Usually the user does not connect directly to the server.

Instead, CyberArk generates an RDP file like:

```
Connect_To_Server01.rdp
```

But the destination is not:

```
Server01
```

It points to:

```
CyberArk PSM Server
```

Example:

Normal RDP:

```
Admin
 |
 | RDP
 |
 ↓
Server01
```

CyberArk RDP:

```
Admin
 |
 | RDP file
 |
 ↓
CyberArk PSM
 |
 | RDP
 |
 ↓
Server01
```

The RDP file becomes the "bridge" into the protected session.

---

# Why does CyberArk use RDP files?

Because CyberArk needs a way to:

✅ Start a remote session  
✅ Send the user through PSM  
✅ Apply security policies  
✅ Record the session  
✅ Prevent password exposure

The RDP file contains the instructions:

> "Do not connect directly to the server. Connect through CyberArk PSM."

---

# Simple analogy

Think of a bank vault.

Without CyberArk:

```
Employee
   |
   | has vault key
   ↓
Safe
```

Problem:

- Employee can lose the key
    
- Someone can steal it
    

With CyberArk:

```
Employee
    |
    | requests access
    ↓
Security guard (PSM)
    |
    | opens vault
    ↓
Safe
```

The employee never gets the key.

The **RDP file is like the appointment ticket that sends you to the security guard instead of directly to the vault.**

---

## In CyberArk terminology:

|Term|Meaning|
|---|---|
|RDP|Protocol used to remotely control Windows machines|
|RDP file|Configuration file that starts an RDP connection|
|PSM|CyberArk component that controls and records privileged sessions|
|Target machine|The server you want to access|
|Vault|Stores and protects privileged credentials|

For a CyberArk beginner, the most important idea is:

> **An RDP file is not the remote connection itself. It is a set of instructions that tells Remote Desktop how and where to connect. In CyberArk, it is usually used to route users through PSM instead of connecting directly to privileged servers.**