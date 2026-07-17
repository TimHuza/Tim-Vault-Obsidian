#cyberark-labs 


![[ui-and-workflows-params.png|239]]

# Imagine You Have a Secret Treehouse 🏠

Only trusted friends are allowed inside.

The treehouse has:

- A door 🚪
    
- A guest list 📋
    
- A security camera 📷
    
- A walkie-talkie 📞
    
- A rulebook 📖
    

UI & Workflows is like the **rulebook** for your treehouse.

Let's go through each section.

---

# 1. Properties

Think of this as:

> **The basic rules for how this platform behaves.**

This section contains general settings about the platform's user interface and workflows.

It answers questions like:

- Which actions are enabled?
    
- Which actions are hidden?
    
- What features should CyberArk use?
    

It's like the "Settings" menu on your phone.

---

### Example

You may decide:

✅ Allow users to connect

✅ Allow password retrieval

❌ Don't allow deleting accounts

CyberArk follows these rules.

---

### Think of it like...

The settings menu in Minecraft.

You can turn things ON or OFF.

---

# 2. Linked Accounts

This one confuses many beginners, but it's actually simple.

Imagine you have **two keys**.

🔑 Key #1 opens the front door.

🔑 Key #2 opens the safe inside.

Sometimes you need both.

CyberArk has the same idea.

Some accounts **depend on another account**.

These are called **Linked Accounts**.

---

### Example

Suppose CyberArk needs to change the password for:

```
Windows Administrator
```

But first it must log into Windows using another special account called:

```
Domain Admin
```

CyberArk links them together.

```
Domain Admin
        │
        ▼
Windows Administrator
```

Now CyberArk knows:

> "Use this account to manage that account."

---

### Why do we need it?

Because sometimes an account **cannot manage itself**.

It needs another account with more permissions.

---

### Think of it like...

Your little brother can't drive.

Your dad drives him to school.

Dad is the **Linked Account**.

---

# 3. Usages

This section answers one question:

> **What is this account allowed to be used for?**

CyberArk stores many different accounts.

Some are used for:

- Password changes
    
- Password verification
    
- Reconciliation
    
- Login
    
- Applications
    
- PSM connections
    

CyberArk needs to know their purpose.

---

### Example

One account is used only for:

```
Password Verification
```

Another account is used only for:

```
Password Change
```

CyberArk keeps everything organized.

---

### Think of it like...

Different tools in a toolbox.

🪛 Screwdriver

🔨 Hammer

🔧 Wrench

Each tool has a different job.

Accounts are the same.

---

# 4. Ticketing System

Imagine your teacher says:

> "Before borrowing the classroom iPad,  
> you must show me your permission slip."

CyberArk can work exactly like that.

Before someone gets a password...

CyberArk asks:

> "Do you have an approved ticket?"

---

A ticket could come from:

- ServiceNow
    
- Jira
    
- Remedy
    
- Another IT system
    

---

Example

Tim wants the Windows Administrator password.

CyberArk asks:

```
Ticket Number?
```

Tim enters:

```
INC-12345
```

CyberArk checks.

✅ Ticket is valid.

Password is released.

---

If there is no ticket...

❌ Access denied.

---

### Why do companies use this?

Because they want proof that someone had permission.

---

### Think of it like...

Borrowing a library book.

You need your library card.

---

# 5. Privileged Session Management (PSM)

This is one of CyberArk's coolest features.

Imagine your parents say:

> "You can play on the family computer...  
> but we're going to watch everything you do."

That's exactly what PSM does.

---

Normally...

A user asks for the password.

CyberArk gives it.

The user logs in.

CyberArk cannot see what happens afterward.

---

With PSM...

CyberArk says:

> "Don't worry about the password."

Instead...

CyberArk opens the connection for you.

```
User
   │
   ▼
CyberArk PSM
   │
   ▼
Server
```

CyberArk can now:

- Record the session 🎥
    
- Watch commands 📝
    
- Monitor activity 👀
    
- End the session if needed ⛔
    

---

### Why is this useful?

Imagine an administrator accidentally deletes a folder.

CyberArk has the recording.

The company can see exactly what happened.

---

### Think of it like...

A security camera in a bank.

It records everything.

---

# 6. Connection Components

This tells CyberArk:

> **"How should we connect to this type of machine?"**

Different systems need different ways to connect.

Examples:

Windows

➡️ RDP

Linux

➡️ SSH

Web

➡️ Browser

Databases

➡️ SQL client

---

CyberArk needs to know:

> "Which connection should I use?"

---

### Example

Windows Platform

```
Use RDP
```

Linux Platform

```
Use SSH
```

Database Platform

```
Use SQL connection
```

CyberArk chooses the correct tool automatically.

---

### Think of it like...

Different keys open different locks.

🚪 House key

🚗 Car key

📬 Mailbox key

CyberArk picks the correct "key."

---

# Putting It All Together

Imagine you click **Connect** to a Linux server.

CyberArk follows the rules in this order:

```
User clicks Connect
        │
        ▼
Properties
"Is Connect allowed?"
        │
        ▼
Ticketing
"Do they have an approved ticket?"
        │
        ▼
Linked Accounts
"Do I need another account first?"
        │
        ▼
Usages
"What is this account used for?"
        │
        ▼
Connection Components
"Use SSH."
        │
        ▼
PSM
"Open the session and record it."
        │
        ▼
Linux Server
```

Everything works together to make access **secure, controlled, and easy to audit**.

---

# Easy Way to Remember

|Section|Simple Question It Answers|Real-Life Example|
|---|---|---|
|**Properties**|What rules should this platform follow?|Phone settings|
|**Linked Accounts**|Does this account need another account to help it?|Dad driving little brother|
|**Usages**|What job is this account meant to do?|Different tools in a toolbox|
|**Ticketing System**|Does the user have permission (a ticket)?|Library card or permission slip|
|**Privileged Session Management (PSM)**|Should CyberArk open and record the session?|Security camera|
|**Connection Components**|How do we connect to the target system?|Using the correct key for the correct lock|

## The Big Picture

Think of **UI & Workflows** as the **instruction manual** for users interacting with accounts. It answers questions like:

- **What actions are allowed?** (Properties)
    
- **Does this account depend on another account?** (Linked Accounts)
    
- **What is this account's job?** (Usages)
    
- **Do we need approval before access?** (Ticketing System)
    
- **Should CyberArk monitor the session?** (PSM)
    
- **How do we connect to the target?** (Connection Components)
    

Together, these settings help CyberArk provide secure, controlled, and well-organized access to privileged accounts.