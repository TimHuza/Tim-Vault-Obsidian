#cyberark-labs 

# Imagine There Were NO Platforms

Let's pretend CyberArk had no Platforms.

You add your first account:

```
Windows Administrator
```

CyberArk asks:

> "How should I change the password?"

You have to answer.

```
Use Windows API.
```

---

Now you add another Windows Administrator account.

CyberArk asks again:

> "How should I change this password?"

You answer again.

```
Use Windows API.
```

---

You add another one.

CyberArk asks again.

```
Use Windows API.
Password length: 20
Rotate every 30 days
Verify password
```

Again...

Again...

Again...

Imagine doing this for **1,000 servers**.

😫 That would take forever!

---

# Platforms Solve This Problem

Instead of configuring every account separately...

You configure the rules **once**.

```
Windows Platform

✔ Password = 20 characters
✔ Rotate every 30 days
✔ Verify password
✔ Use Windows API
```

Now every Windows account can use the same Platform.

```
Windows Platform
       │
       ├── Server1 Administrator
       ├── Server2 Administrator
       ├── Server3 Administrator
       ├── Server4 Administrator
       ├── Server5 Administrator
       └── ...
```

CyberArk doesn't need you to repeat yourself.

---

# Real Life Example

Imagine your teacher says:

> Everyone in class must wear a school uniform.

Does the teacher go to every student and say:

```
Tim,
wear blue pants.

Emma,
wear blue pants.

John,
wear blue pants.

Sarah,
wear blue pants.
```

No.

The teacher makes **one rule**.

```
School Uniform
```

Everyone follows it.

A Platform is exactly like that.

---

# Another Example

Imagine you own a zoo.

You have

🐘 20 elephants

🦒 15 giraffes

🐒 50 monkeys

Would you write feeding instructions for every single elephant?

No.

You write one instruction sheet.

```
Elephant Rules

Food:
Hay

Water:
100 L

Feed:
Twice a day
```

Every elephant follows the same instructions.

CyberArk works exactly the same way.

---

# Let's Imagine a Company

Suppose Microsoft has:

- 5,000 Windows servers
    
- 2,000 Linux servers
    
- 600 Oracle databases
    

That's over **7,600 privileged accounts**.

Without Platforms...

Someone would need to configure:

- password length
    
- password complexity
    
- rotation
    
- verification
    
- plugins
    

...for **every single account**.

That would be a nightmare.

---

With Platforms...

```
Windows Platform
```

applies to all Windows accounts.

```
Linux Platform
```

applies to all Linux accounts.

```
Oracle Platform
```

applies to all Oracle accounts.

Much easier.

---

# Another Huge Benefit

Imagine your company changes its security policy.

Old rule:

```
Passwords = 12 characters
```

New rule:

```
Passwords = 20 characters
```

Without Platforms...

Someone has to edit

```
Server 1

Server 2

Server 3

Server 4

...
Server 5000
```

One by one.

😱

---

With Platforms...

You change **one setting**.

```
Windows Platform

Password Length

12

↓

20
```

Done.

Every Windows account now follows the new rule.

That's incredibly powerful.

---

# Another Benefit

Different systems work differently.

Windows changes passwords one way.

Linux changes passwords another way.

Oracle databases use a different method.

Cisco routers use another.

CyberArk needs to know **which method** to use.

Platforms tell CyberArk exactly how to talk to each system.

For example:

```
Windows Platform
↓
Uses Windows password-change plugin
```

```
Unix Platform
↓
Uses SSH
```

```
Oracle Platform
↓
Uses Oracle SQL commands
```

Without Platforms, CyberArk wouldn't know which "language" to speak to each system.

---

# Think of Platforms Like a Remote Control

Imagine you have

📺 TV

❄ Air Conditioner

🔊 Speaker

Can one remote control work for everything?

Only if it knows how each device works.

CyberArk is like a universal remote.

Platforms teach it:

```
TV

Press these buttons.
```

```
Air Conditioner

Use these buttons.
```

```
Speaker

Use these buttons.
```

Without those instructions, the remote wouldn't know what to do.

---

# The Big Picture

```text
          Company
              │
              ▼
       Hundreds or thousands
      of privileged accounts
              │
              ▼
     Which rules should they follow?
              │
              ▼
        Assign a Platform
              │
              ▼
 +------------------------------+
 | Windows Platform             |
 | • 20-character passwords     |
 | • Rotate every 30 days       |
 | • Verify password            |
 | • Use Windows plugin         |
 +------------------------------+
              │
              ▼
 All Windows accounts follow
 the same rules automatically.
```

---

# Why Do We Need Platforms?

We need Platforms because they:

- 📋 **Store rules in one place** instead of configuring every account individually.
    
- 🔄 **Apply the same rules** to many accounts of the same type.
    
- ⚡ **Save time** by eliminating repetitive configuration.
    
- 🛡️ **Keep security consistent**, so similar accounts follow the same policies.
    
- 🔧 **Tell CyberArk how to manage each type of system**, because Windows, Linux, databases, and network devices all work differently.
    
- 📈 **Make changes easy**—update one Platform, and every account using it gets the new behavior.
    

---

# The One-Sentence Answer

> **We need Platforms because CyberArk manages many different types of accounts, and a Platform gives CyberArk one reusable set of instructions that can be applied to all similar accounts. This saves time, keeps security consistent, and tells CyberArk exactly how to manage each type of system.**

This is one of the core ideas in CyberArk. Once you understand _why_ Platforms exist, you'll find it much easier to understand related concepts like **CPM**, **PSM**, **account onboarding**, and **password rotation**, because they all rely on the Platform's instructions.