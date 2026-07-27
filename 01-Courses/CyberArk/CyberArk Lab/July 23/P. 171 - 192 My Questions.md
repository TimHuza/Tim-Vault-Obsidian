#cyberark-labs 

# 1. What is EPV? (Page 171)

**EPV** stands for:

> **Enterprise Password Vault**

This is the **heart** of CyberArk.

Think of CyberArk like a giant castle.

Inside the castle is the **Vault**, where all the important passwords are stored safely.

```text
              CyberArk

      +-----------------------+
      |                       |
      |       EPV Vault       |
      |                       |
      |  Windows Passwords    |
      |  Linux Passwords      |
      |  Database Passwords   |
      |  Service Accounts     |
      |                       |
      +-----------------------+
```

Instead of writing passwords on sticky notes...

CyberArk stores them inside the EPV.

Nobody can simply walk in and read them.

---

## What does EPV do?

EPV stores things like:

- Windows Administrator passwords
    
- Linux Root passwords
    
- Database passwords
    
- Service Account passwords
    
- SSH Keys
    
- Secrets
    

Think of it like a giant bank vault.

Instead of money...

it stores **passwords**.

---

## Why do we need EPV?

Imagine a company has:

- 2,000 servers
    
- 500 administrators
    
- 15,000 privileged passwords
    

Keeping those passwords in Excel would be dangerous.

Instead...

```text
Admin
   │
   ▼
CyberArk EPV
   │
   ▼
Password is securely stored
```

The password never needs to be memorized.

CyberArk protects it.

---

## Beginner Summary

> **EPV is CyberArk's giant secure vault that stores privileged passwords safely.**

---

# 2. What is EPV Transparent Connection? (Page 171)

This sounds complicated...

but it's actually very simple.

Imagine you want to connect to a Windows server.

Normally...

You would need to know:

- Username
    
- Password
    

Like this:

```text
User
   │
Enter Password
   │
   ▼
Server
```

But CyberArk says:

> "Don't worry.  
> I'll enter the password for you."

Now it becomes:

```text
User
   │
Click Connect
   │
   ▼
CyberArk
   │
Gets password from EPV
   │
Logs in automatically
   │
   ▼
Server
```

You never type the password.

Sometimes...

you never even **see** the password.

CyberArk does everything behind the scenes.

That's why it's called a **Transparent Connection**.

It is "transparent" because the password is hidden from the user.

---

### Think of it like this

Imagine a hotel.

Instead of giving you the master key...

The hotel employee unlocks the room for you.

You enter.

But you never touch the master key.

CyberArk works exactly like that.

---

## Beginner Summary

> **Transparent Connection means CyberArk logs into the target system for you without showing you the password.**

---

# 3. What are Exceptions? How? Purpose? (Page 173)

Earlier we learned that PSM can protect:

- Everyone
    
- Only selected accounts
    

Those selected accounts are called **Exceptions**.

---

Imagine your school says:

> Everyone wears a school uniform.

Later...

The principal changes the rule.

Only these students wear uniforms:

- John
    
- Sarah
    
- Alex
    

Those students are the **exceptions**.

---

CyberArk works exactly the same way.

Suppose PSM is OFF globally.

Normally:

```text
Everyone
   │
Direct Login
```

But then CyberArk says:

Except...

```text
Windows Admin
Database Admin
Root Account
```

Those accounts must still use PSM.

```text
Windows Admin
      │
      ▼
     PSM

Linux Root
      │
      ▼
Direct Login
```

---

## Why use Exceptions?

Companies may only want to monitor their most important systems.

Examples:

✅ Domain Controllers

✅ Database Servers

✅ Production Servers

But not:

❌ Test Servers

❌ Lab Machines

❌ Temporary Accounts

Exceptions let CyberArk protect only the accounts that really matter.

---

## Beginner Summary

> **Exceptions are a list of special accounts that still use PSM even when everyone else does not.**

---

# 4. What is PSM HTML5 Gateway? (Page 176)

Normally...

When connecting to a Windows server...

Your computer needs software like:

- Remote Desktop (RDP)
    
- mstsc.exe
    

But sometimes you're using:

- Chrome
    
- Edge
    
- Firefox
    

and you don't want to install anything.

That's where the **PSM HTML5 Gateway** comes in.

---

Instead of this:

```text
Your PC
     │
mstsc.exe
     │
     ▼
PSM
     │
Server
```

You do this:

```text
Browser
     │
     ▼
HTML5 Gateway
     │
     ▼
PSM
     │
     ▼
Server
```

Everything happens inside the web browser.

No Remote Desktop program is needed.

---

Think about YouTube.

Years ago you needed Adobe Flash.

Now...

Videos play directly in your browser.

The HTML5 Gateway works the same way.

It lets Remote Desktop sessions run in the browser.

---

## Beginner Summary

> **The PSM HTML5 Gateway lets you connect to servers through a web browser without installing Remote Desktop software.**

---

# 5. How does the drag-and-drop process work between `acme-123.acme.com` and `main-comp01`? (Page 182)

Imagine these two computers:

```text
Your Computer
(main-comp01)

Server
(acme-123.acme.com)
```

Normally...

Windows lets you drag files between them.

Like this:

```text
PDF
 │
 ▼
Drag
 │
 ▼
Server
```

But CyberArk is very careful.

Why?

Because someone could steal company files.

Or upload dangerous files.

Instead...

The file first goes through the PSM server.

```text
Your Computer
      │
      ▼
     PSM
      │
(Security checks)
      │
      ▼
Target Server
```

The PSM controls whether drag and drop is allowed based on company policy.

Some companies:

✅ Allow uploads

Some:

❌ Block uploads

Some:

✅ Allow downloads only

Everything is controlled by CyberArk.

---

## Why?

Imagine an administrator accidentally drags:

```text
virus.exe
```

onto a production server.

That could be a disaster.

CyberArk can stop that from happening.

---

## Beginner Summary

> **When you drag and drop files during a PSM session, CyberArk controls the transfer and can allow, block, or monitor it to keep systems secure.**

---

# 6. What is `mstsc`? (Page 186)

`mstsc` is a Windows program.

Its full name is:

> **Microsoft Terminal Services Client**

Most people simply call it:

> **Remote Desktop**

If you press:

```text
Windows + R
```

and type:

```text
mstsc
```

Windows opens Remote Desktop.

```text
Windows Computer
      │
      ▼
Remote Desktop (mstsc)
      │
      ▼
Another Windows Server
```

Without CyberArk:

```text
Your Computer
      │
      ▼
mstsc
      │
      ▼
Windows Server
```

With CyberArk:

```text
Your Computer
      │
      ▼
mstsc
      │
      ▼
PSM
      │
      ▼
Windows Server
```

Notice the difference:

CyberArk sits in the middle and watches the session.

It can:

- 🎥 Record everything you do.
    
- 🔑 Retrieve the password from the EPV.
    
- 🛡️ Enforce security policies.
    
- 📋 Log who connected and when.
    

---

## Beginner Summary

> **`mstsc` is the built-in Windows Remote Desktop program that lets you connect to another Windows computer. When used with CyberArk, it connects through the PSM so the session can be secured and monitored.**

---

# 🎯 Big Picture: How Everything Connects

```text
                Administrator
                      │
                      ▼
            Click "Connect" in PVWA
                      │
                      ▼
      EPV retrieves the password securely
                      │
                      ▼
      Transparent Connection (no password shown)
                      │
                      ▼
        PSM (records and protects session)
              │                  │
              │                  └── Can use HTML5 Gateway
              │                      (browser connection)
              ▼
        mstsc (or browser session)
              │
              ▼
   Target Server (acme-123.acme.com)

During the session:
 • Drag & Drop (if allowed by policy)
 • Clipboard (if allowed)
 • Session Recording
 • Keystroke Monitoring

Exceptions decide **which accounts** must go through PSM when PSM isn't required for everyone.
```