#cyberark-labs 

# First, what is a Platform?

Imagine you have a **toy box**.

Inside the toy box you have different toys:

- 🚗 Cars
    
- 🦖 Dinosaurs
    
- 🤖 Robots
    
- 🧸 Teddy bears
    

Each toy is different.

You wouldn't store a dinosaur the same way you store a robot.

Each toy needs its own rules.

---

CyberArk works exactly the same way.

Instead of toys, CyberArk stores **accounts**.

For example:

- Windows Administrator
    
- Linux root
    
- Oracle Database account
    
- Cisco router account
    
- AWS account
    
- Azure account
    

Each one behaves differently.

So CyberArk needs instructions for each type.

Those instructions are called a **Platform**.

---

# Simple Definition

> A **Platform** is a set of rules that tells CyberArk how to manage a certain type of account.

That's it.

Think of a platform as a **recipe** or an **instruction manual**.

---

# Imagine This

Pretend you're working in a pet store.

You take care of

🐶 Dogs

🐱 Cats

🐟 Fish

Do you feed them all the same food?

No.

Dogs eat dog food.

Cats eat cat food.

Fish eat fish food.

Each animal has different instructions.

CyberArk does the same thing.

Different account = different instructions.

Those instructions are the Platform.

---

# Example

Suppose someone adds this account:

```
Server:
Windows Server 2022

Username:
Administrator
```

CyberArk asks itself:

> "How do I manage a Windows Administrator account?"

It looks for the

```
Windows Server Platform
```

Inside that platform are all the answers.

---

# What kinds of instructions are inside a Platform?

A platform can tell CyberArk things like

✅ How to change the password

Example:

```
Click here
Run PowerShell
Use Windows API
```

---

It can also say

✅ How often to rotate passwords

Example

```
Every 30 days
```

---

It can also say

✅ Password length

Example

```
20 characters
```

---

It can also say

✅ Password complexity

Example

```
Uppercase

Lowercase

Numbers

Special characters
```

---

It can also say

✅ Whether password verification is enabled

CyberArk can log in using the new password to make sure it actually works.

---

It can also say

✅ Which plugin should be used

For Windows:

```
Windows plugin
```

For Linux:

```
SSH plugin
```

For Oracle:

```
Oracle plugin
```

---

# Think of it like a Robot

Imagine CyberArk is a robot.

The robot doesn't know anything.

You tell it:

```
When you see Windows,
do this.

When you see Linux,
do this.

When you see Oracle,
do this.
```

Those instructions are Platforms.

---

# What happens when you add an account?

Let's walk through it.

---

## Step 1

You add an account.

Example

```
Administrator

Windows Server
```

---

## Step 2

CyberArk asks

> Which platform should I use?

You select

```
WinServerLocal
```

---

## Step 3

CyberArk loads all the rules.

Maybe it finds

```
Password length = 25

Rotate every 30 days

Verify after change

Use Windows Password Change plugin
```

---

## Step 4

CyberArk follows those rules forever.

Every time it needs to change or verify the password...

It uses the Platform.

---

# Real Example

Imagine two accounts.

---

Windows

```
Administrator
```

Platform

```
Windows Server Platform
```

Instructions

```
Rotate every 30 days

Use Windows plugin

Password = 25 characters
```

---

Linux

```
root
```

Platform

```
Unix SSH Platform
```

Instructions

```
Rotate every 60 days

Connect using SSH

Password = 32 characters
```

---

Notice something?

The accounts are different.

The instructions are different.

That's [[Why Need Platforms|why we need different Platforms]].

---

# A Real-Life Analogy

Imagine you're cooking.

You have

🍕

Pizza

🍰

Cake

Do you use the same recipe?

No.

Pizza recipe

↓

Dough

Cheese

Tomato sauce

Bake 15 minutes

---

Cake recipe

↓

Flour

Sugar

Eggs

Bake 45 minutes

---

The recipe tells you exactly what to do.

A Platform is simply CyberArk's recipe.

---

# Where do Platforms live?

Inside the CyberArk PVWA, you'll find a section called **Platforms**.

There you can see many predefined platforms, such as:

- Windows Local
    
- Unix SSH
    
- Oracle Database
    
- Microsoft SQL Server
    
- VMware
    
- AWS
    
- Azure
    
- Cisco devices
    

CyberArk already includes many built-in platforms so you don't have to create them from scratch.

---

# Can many accounts use one Platform?

Yes!

Imagine you have 500 Windows servers.

Each server has an

```
Administrator
```

account.

Do you create 500 different platforms?

No.

You create **one Windows Platform**, and all 500 accounts can use it.

```
Platform
     │
     ├── Server 1 Administrator
     ├── Server 2 Administrator
     ├── Server 3 Administrator
     ├── Server 4 Administrator
     └── Server 500 Administrator
```

This makes management much easier. If you change the platform (for example, increase the password length), every account using that platform will follow the new rule.

---

# What is inside a Platform?

A Platform can contain settings such as:

|Setting|What it tells CyberArk|
|---|---|
|Password length|How long the password should be|
|Password complexity|Uppercase, lowercase, numbers, symbols|
|Password rotation|How often to change the password|
|Verification|Check that the new password works|
|Reconciliation|Recover or fix passwords if they become out of sync|
|Connection method|SSH, RDP, Windows API, database connection, etc.|
|Password change plugin|The method or plugin used to change the password|
|Allowed characters|Which characters can appear in passwords|

---

# The Big Picture

```text
             You add an account
                     │
                     ▼
        +-----------------------+
        | Windows Administrator |
        +-----------------------+
                     │
                     ▼
      CyberArk asks:
      "Which Platform should I use?"
                     │
                     ▼
       +------------------------+
       | Windows Platform       |
       +------------------------+
       | Password: 25 chars     |
       | Rotate: 30 days        |
       | Verify: Yes            |
       | Plugin: Windows        |
       +------------------------+
                     │
                     ▼
     CyberArk follows these rules
     whenever it manages the account.
```

---

# The One-Sentence Definition

> **A Platform is a reusable set of rules and instructions that tells CyberArk how to manage a specific type of account, including how to change, verify, reconcile, and secure its password.**

As you continue your CyberArk lab, you'll notice that **every account belongs to a Platform**. The Platform acts like the account's **instruction manual**—CyberArk reads that manual whenever it needs to manage the account. Once you understand Platforms, many other CyberArk concepts (like password rotation, verification, CPM plugins, and account onboarding) become much easier to understand.