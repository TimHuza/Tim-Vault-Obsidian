#cyberark-labs 


![[params-dom-cybr-15.png|305]]
# Imagine You Have a Toy Safe

Inside your safe you keep your most valuable toys.

The safe doesn't just hold toys.

It also has **rules**, like:

- Who can open it?
    
- How often should the lock change?
    
- What happens after someone uses a toy?
    
- Should we record who opened it?
    

In CyberArk, a **Platform** is exactly like those rules.

When you edit a platform, you're telling CyberArk:

> "Whenever you manage accounts of this type, follow these rules."

The sections you're asking about are groups of those rules.

---

# 1. [[UI & Workflows (Parameters)|UI & Workflows]]

Think of this as:

> **"How should people interact with these accounts?"**

This section controls what users see and what actions they are allowed to perform.

For example:

- Can users change the password?
    
- Can they reconcile the account?
    
- Can they verify it?
    
- Which buttons appear in PVWA?
    
- What workflow should happen?
    

### Example

Suppose your platform is for Windows Administrator accounts.

Maybe you want users to be able to:

✅ Connect

✅ View password

✅ Change password

But maybe you don't want them deleting accounts.

So **UI & Workflows** decides:

> "Which actions are available?"

---

### Think of it like a video game menu.

When you open Minecraft, you see buttons like:

- Single Player
    
- Multiplayer
    
- Options
    

You don't see every hidden developer button.

CyberArk is the same.

UI & Workflows decides which buttons users see.

---

# 2. [[Automatic Password Management (Params)|Automatic Password Management]]

This is one of the MOST IMPORTANT parts of CyberArk.

Think of it like this.

Imagine your mom says:

> "Every Friday, change the password on the family tablet."

Instead of your mom doing it...

A robot does it automatically.

That's exactly what this section controls.

---

It answers questions like:

- Should CyberArk automatically change passwords?
    
- How often?
    
- How?
    
- What happens if it fails?
    
- Should it verify the new password afterward?
    

---

## Example

Let's say a Windows Administrator password is:

```
Password123
```

CyberArk logs in.

Changes it to:

```
Yt8!Qz94#Lm
```

Stores the new password.

Tests it.

Everything works.

Done.

Nobody had to do anything.

---

Without this feature...

Someone would have to change hundreds or thousands of passwords manually.

Imagine changing passwords for:

- 500 Windows servers
    
- 300 Linux servers
    
- 200 SQL databases
    

That would take forever.

CyberArk automates it.

---

### Think of it like...

An automatic toothbrush.

Instead of brushing yourself...

The toothbrush does all the work.

CyberArk changes passwords for you.

---

# 3. General Properties

This section contains the platform's **general settings**.

Think of it as the platform's **ID card**.

It tells CyberArk things like:

- What is this platform called?
    
- What platform ID does it use?
    
- Is it active?
    
- What kind of accounts belong here?
    
- Other basic information.
    

---

Imagine you're creating a folder.

The folder needs:

- A name
    
- A color
    
- A label
    
- A description
    

General Properties is like filling out those details.

---

# Why are these sections separated?

Imagine your school.

The principal has different folders.

📁 Student Information

📁 Teachers

📁 Timetable

📁 Sports

Everything isn't thrown into one giant folder.

CyberArk does the same.

Instead of 300 settings in one place, it groups them.

|Section|What it controls|
|---|---|
|UI & Workflows|What users can do|
|Automatic Password Management|How CyberArk changes passwords|
|General Properties|Basic information about the platform|

---

# A Real CyberArk Example

Imagine you create a platform called:

```
Windows Server Accounts
```

### General Properties

You tell CyberArk:

> This platform manages Windows Server accounts.

---

### Automatic Password Management

You tell CyberArk:

- Change passwords every 30 days.
    
- Verify the password afterward.
    
- Retry if something fails.
    

---

### UI & Workflows

You tell CyberArk:

- Show the **Connect** button.
    
- Allow **Change Password**.
    
- Allow **Verify Password**.
    
- Hide actions users shouldn't perform.
    

---

Now every Windows Server account that uses this platform follows those same rules automatically.

---

# Easy Way to Remember

Imagine a **remote-controlled robot**.

🤖 **General Properties**

> "Who are you?"

(Name, ID, basic information.)

---

🎮 **UI & Workflows**

> "What buttons can people press?"

(Connect, Verify, Change Password, etc.)

---

🔐 **Automatic Password Management**

> "How do you take care of passwords automatically?"

(Change them, verify them, retry if needed.)

---

## The Big Picture

Every account assigned to a platform inherits these rules.

For example:

```
Platform
│
├── General Properties
│      "Who am I?"
│
├── UI & Workflows
│      "What can users do?"
│
└── Automatic Password Management
       "How do I manage passwords?"
            │
            ▼
      Every account using this platform
      follows these rules automatically.
```

As you continue exploring the Platform Editor, we can also go through **every single setting inside each section** (for example, every option under **Automatic Password Management**) one by one in beginner-friendly language. That's how CyberArk professionals typically learn the platform.