#cyberark-labs 
[[Reports questions]]

# 📊 What are Reports?

Imagine your teacher asks:

> **"Can you show me who borrowed books from the library this week?"**

Instead of asking every student one by one, the librarian prints a **report**.

A **report** is simply a document that shows information collected by CyberArk.

It answers questions like:

- Who logged in?
    
- Who used an account?
    
- Which passwords changed?
    
- Did anything fail?
    
- Is everything working correctly?
    

So a report is like CyberArk's **report card** or **activity summary**.

---

# 🏢 Real World Example

Imagine a company has:

- 5,000 employees
    
- 20,000 servers
    
- 100,000 privileged accounts
    

Every day thousands of things happen.

Without reports, the administrator would have to look through millions of events.

Instead CyberArk creates reports automatically.

Example:

```
Today's Report

✔ 52 passwords changed
✔ 13 new accounts onboarded
✔ 4 failed login attempts
✔ 7 PSM sessions recorded
✔ Everything healthy
```

Much easier!

---

# Why do we need Reports?

Reports help administrators answer questions quickly.

For example:

### Is CyberArk working?

```
Password changes today:
✔ Success: 125
❌ Failed: 2
```

Good!

---

### Did someone log into a server?

```
Tom
Logged into Server01
2:15 PM
Through PSM
```

Easy to find.

---

### Did anyone break security rules?

```
Failed logins:
Mike
10 failed attempts
```

Maybe someone guessed the password.

The administrator should investigate.

---

# How Reports Work

Let's see the whole process.

```
User logs into server
        │
        ▼
CyberArk records the event
        │
        ▼
Stores information inside the Vault
        │
        ▼
Report collects the information
        │
        ▼
Administrator opens report
```

Think of it like:

```
Security Camera
        │
        ▼
Records everything
        │
        ▼
Creates a summary
        │
        ▼
Boss reads summary
```

CyberArk does exactly that.

---

# There are three main types of reports

Think of a school.

Different people need different information.

Teacher wants grades.

Principal wants attendance.

Parents want homework.

CyberArk is the same.

---

# 1️⃣ Operational Reports

These answer:

> **"Is CyberArk working properly?"**

These reports focus on daily operations.

Examples:

- Password changes
    
- Password verification
    
- Password reconciliation
    
- Failed CPM jobs
    
- Successful CPM jobs
    
- Discovery results
    

Example:

```
Password Changes

Server01 ✔
Server02 ✔
Server03 ✔
Server04 ❌ Failed
```

The administrator immediately knows something needs fixing.

Think of this as:

> A mechanic checking if every part of a car works.

---

# 2️⃣ Audit / Compliance Reports

These answer:

> **"Who did what?"**

Companies must follow security rules.

Auditors often ask:

- Who logged in?
    
- When?
    
- Which account?
    
- Which server?
    
- Was the session recorded?
    

CyberArk keeps all this information.

Example:

```
User:
Tom

Account:
Administrator

Server:
Server01

Time:
3:15 PM

Session Recorded:
Yes
```

Months later someone can still see exactly what happened.

Think of it like:

A security camera.

If something goes wrong...

You watch the recording.

CyberArk's audit reports work the same way.

---

# Why are they called Compliance reports?

Many companies must obey laws or standards.

For example:

- Banks
    
- Hospitals
    
- Governments
    

They must prove:

> "We protected our privileged accounts."

CyberArk reports provide that proof.

Without them:

```
Auditor:
Who used Administrator yesterday?

Company:
...

We don't know.
```

That would be a serious problem.

---

# 3️⃣ List Reports

These simply show lists of objects.

Examples:

- All Safes
    
- All users
    
- All platforms
    
- All accounts
    
- All onboarded machines
    

Example:

```
Accounts

Administrator
root
OracleAdmin
SQLAdmin
BackupAdmin
```

Or:

```
Safes

Windows
Linux
Database
Network
Cloud
```

Nothing is happening here.

It is simply a list.

Think of it like:

A class roster.

```
Students

Tom
Sarah
John
Emily
```

Just information.

---

# Easy way to remember

|Report Type|Question it Answers|
|---|---|
|Operational|Is everything working?|
|Audit / Compliance|Who did what?|
|List|What do we have?|

---

# 🗂️ What is the Vault.ini file?

This is one of the most important files in CyberArk.

Imagine you have a treasure map.

The map says:

```
Treasure is here.

Street:
123 Pirate Road

Key:
Gold

Door:
Blue
```

Without the map...

Nobody knows where the treasure is.

The **Vault.ini** file is like that treasure map.

---

It tells CyberArk:

> "This is where the Digital Vault is."

---

# What information is inside Vault.ini?

It usually contains information like:

- Vault server address (IP or hostname)
    
- Vault communication port
    
- Connection settings
    

Example (simplified):

```ini
[Vault]

Address=192.168.1.10
Port=1858
```

This tells CyberArk:

```
Vault lives at

192.168.1.10

Use port

1858
```

---

# Why do we need Vault.ini?

Imagine trying to call your friend.

If you don't know their phone number...

You can't call them.

Same idea.

CyberArk components need to know:

- Where is the Vault?
    
- Which port should I use?
    
- How do I connect?
    

Vault.ini answers those questions.

Without it...

```
CPM

↓

"I don't know where the Vault is."

Connection Failed
```

---

# How Vault.ini Works

Suppose the CPM service starts.

Step 1

```
CPM starts
```

↓

Step 2

```
Reads Vault.ini
```

↓

Step 3

```
Learns Vault IP

192.168.1.10
```

↓

Step 4

```
Connects to the Vault
```

↓

Step 5

```
Reads passwords
```

↓

Step 6

```
Starts working
```

Every CyberArk component does something similar when it needs to communicate with the Vault.

---

# Think of Vault.ini like a GPS

Without GPS:

```
"Where is the Vault?"
```

Nobody knows.

With GPS:

```
Vault

192.168.1.10

Port 1858
```

Connection succeeds.

---

# Simple Analogy

Imagine a school.

🏫 **The Vault** = Principal's office (where important documents are stored)

👨‍🏫 **CPM, PVWA, PSM** = Teachers who need to visit the principal.

📄 **Vault.ini** = A note that says:

```
Principal's Office

Room 101

Second Floor

Door Number 3
```

Without the note, teachers wander around the school trying to find the office.

With the note, they go straight there.

---

# 🎯 Quick Summary

## 📊 Reports

- Show information collected by CyberArk.
    
- Help administrators monitor the system, investigate activity, and demonstrate compliance with security policies.
    

## 📈 Operational Reports

- Show whether CyberArk is working correctly.
    
- Examples: password changes, verification, reconciliation, CPM job status.
    

## 🔍 Audit / Compliance Reports

- Record who did what, when, and where.
    
- Used for investigations and proving compliance with security standards.
    

## 📋 List Reports

- Display inventories of CyberArk objects.
    
- Examples: lists of Safes, users, accounts, or platforms.
    

## 🗂️ Vault.ini

- A configuration file that tells CyberArk components how to find and connect to the Digital Vault.
    
- Typically contains the Vault's address, port, and connection settings.
    
- Without it, components like CPM, PSM, and PVWA wouldn't know where the Vault is, so they couldn't communicate with it.