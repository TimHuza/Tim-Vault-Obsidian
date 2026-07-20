#concepts 


![Image|697](https://images.openai.com/static-rsc-4/f1BpcCHAVuVkzA5H_TT-HFldEWIV1CVpjj72p9cX4xDy3-ZAzu6Cyrd08kgmfyJOmxPaIiMSNsdpIfqHq-5V-MdlEyi35e_61CMAmN9UW8VbqU1kvAmI04eUJ8zAAX0q3BURO_FN4zNSzHhIKjpmtK_68tSjK1QJfVa1R0xSQ2O6bI1BPBVijZK2h4f_hmth?purpose=fullsize)
# What is Active Directory (AD)?

Imagine you have a **huge school**.

The school has:

- 👨‍🎓 Students
    
- 👩‍🏫 Teachers
    
- 🖥️ Computers
    
- 🔑 Lockers
    
- 📚 Classrooms
    
- 📋 Rules
    

The school needs a system that answers questions like:

> "Who is this person?"  
> "Are they allowed to enter this classroom?"  
> "Which computer can they use?"  
> "What rules apply to them?"

**Active Directory is like the school's security office.**

It keeps track of all users, computers, and permissions inside a company.

---

# Simple Definition

**Active Directory (AD)** is a Microsoft system that organizations use to:

- 👤 Manage users
    
- 💻 Manage computers
    
- 🔐 Control access
    
- 📜 Apply security rules
    
- 🏢 Organize company resources
    

It is basically a **database + security manager** for a Windows network.

---

# Why do companies need Active Directory?

Imagine a company with:

- 10,000 employees
    
- 5,000 computers
    
- 500 servers
    

Without Active Directory:

Every computer would have its own users and passwords.

Example:

```
Computer-1
    Tim
    Sarah
    John

Computer-2
    Tim
    Sarah
    John

Server-1
    Tim
    Sarah
    John
```

This becomes a nightmare.

If Sarah leaves the company:

Someone has to remove Sarah from thousands of computers.

😱 Impossible.

---

With Active Directory:

The company has **one central place**:

```
              Active Directory
                    |
     --------------------------------
     |              |               |
   Users        Computers       Servers

    Tim           PC-001        SQL Server
    Sarah         PC-002        Web Server
    John          PC-003        File Server
```

Remove Sarah once:

```
Delete Sarah from AD
          |
          ↓
She loses access everywhere
```

Much easier.

---

# Main Components of Active Directory

Let's break it down.

---

# 1. Users 👤

A user is a person or account.

Example:

```
Username:
tim.huza

Password:
********

Department:
IT

Role:
Administrator
```

AD stores information about users:

- Name
    
- Username
    
- Password information
    
- Email
    
- Department
    
- Permissions
    

---

# 2. Computers 💻

AD also knows about computers.

Example:

```
Computer Name:

FINANCE-PC-001

Operating System:

Windows 11

Owner:

Finance Department
```

A computer can join the AD domain.

---

# 3. Groups 👥

Instead of giving permissions one person at a time, AD uses groups.

Example:

Instead of:

```
Give John access
Give Sarah access
Give Mike access
Give Tom access
```

You create:

```
Finance Team Group

Members:
- John
- Sarah
- Mike
- Tom
```

Then:

```
Finance Group
       |
       ↓
Access to Finance Files
```

Much easier.

---

# 4. Organizational Units (OUs) 📁

OUs are like folders used to organize objects.

Example:

Company:

```
Company.com
|
├── IT
│    ├── Users
│    └── Computers
|
├── Finance
│    ├── Users
│    └── Computers
|
└── HR
     ├── Users
     └── Computers
```

This helps administrators manage thousands of objects.

---

# 5. Domain 🌐

A **Domain** is the main "container" of an Active Directory environment.

Example:

Company name:

```
CyberArkLab.com
```

Inside:

```
CyberArkLab.com

Users:
    Tim
    Admin
    Helpdesk

Computers:
    Server01
    PC01
    PC02
```

Everyone belongs to the domain.

---

# 6. Domain Controller (DC) 🖥️

This is the most important part.

A **Domain Controller** is a server running Active Directory.

Think of it as:

> The security guard at the school entrance.

When you log in:

```
You:
"Hello, I am Tim"

Computer:
"Let me ask Active Directory"

Computer
     |
     ↓
Domain Controller

AD:
"Yes, Tim exists.
Password is correct.
Allow login."
```

Then you enter.

---

# How Login Works in Active Directory

Example:

You turn on your company laptop.

You type:

```
Username:
tim.huza

Password:
123456
```

The computer asks:

```
"Hey Domain Controller,
does Tim exist?"
```

AD checks:

```
User:
Tim

Password:
Correct ✅

Group:
IT Administrators

Permissions:
Allowed ✅
```

Then:

```
Access Granted
```

---

# Active Directory and CyberArk (Very Important)

Now let's connect it to CyberArk.

CyberArk protects **privileged accounts**.

Privileged accounts are powerful accounts like:

```
Administrator
Domain Admin
Root
SQL Admin
Service Accounts
```

Active Directory contains these accounts.

Example:

Active Directory:

```
Domain Admins Group

Members:

Administrator
CyberArkAdmin
ServerAdmin
```

These accounts can control everything.

---

The problem:

A hacker steals:

```
Domain Admin
Password:
Password123
```

Now they can:

- Create users
    
- Disable antivirus
    
- Access servers
    
- Install malware
    
- Move around the network
    

This is called:

## Lateral Movement

---

CyberArk helps protect these accounts.

Example:

Without CyberArk:

```
Admin
 |
Password
 |
Everyone knows it
 |
Hacker steals it
```

---

With CyberArk:

```
Administrator Account

        |
        ↓

CyberArk Vault

        |
        ↓

Password stored safely

        |
        ↓

User requests access

        |
        ↓

CyberArk gives temporary access
```

The password is hidden.

---

# Active Directory + CyberArk Example

Company has:

```
Active Directory

Users:
    Bob
    Alice

Privileged Accounts:
    Domain Admin
    Server Admin
    SQL Admin
```

CyberArk manages:

```
Domain Admin
Server Admin
SQL Admin
```

Flow:

1. Admin wants to use Domain Admin account
    
2. They request access in CyberArk
    
3. CyberArk checks:
    

```
Is Bob allowed?
Is approval needed?
How long?
```

4. CyberArk gives access
    
5. CyberArk can automatically change the password afterward
    

Example:

Before:

```
Domain Admin password:

OldPassword123
```

After:

```
NewRandomPassword:
X9#kLm22!pQ
```

Nobody knows it.

---

# Active Directory vs CyberArk

|Active Directory|CyberArk|
|---|---|
|Manages identities|Protects privileged identities|
|Stores users|Stores sensitive passwords|
|Controls login|Controls privileged access|
|Creates groups|Controls privileged accounts|
|Microsoft technology|PAM security platform|

Think:

```
Active Directory
        |
        |
"Who are you?"
        |
        ↓

CyberArk
        |
        |
"What powerful accounts can you use?"
"Are you allowed?"
"How do we protect them?"
```

---

# Easy way to remember

🟦 **Active Directory = Company phone book + security guard**

It knows:

- Who works here
    
- What computers exist
    
- Who can access what
    

🟧 **CyberArk = The bank vault for the most powerful keys**

It protects:

- Administrator passwords
    
- Server passwords
    
- Service accounts
    
- Root accounts
    

---

Since you are learning CyberArk, the next important topics after Active Directory are usually:

1. **Domain Controller (DC)**
    
2. **Domain Admin account**
    
3. **AD Groups**
    
4. **LDAP**
    
5. **How CyberArk connects to Active Directory**
    
6. **CyberArk Safe vs AD permissions**
    

Those are the pieces that make CyberArk labs start making sense.