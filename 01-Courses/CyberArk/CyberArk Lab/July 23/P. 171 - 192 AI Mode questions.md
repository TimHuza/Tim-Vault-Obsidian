#cyberark-labs 


# 1. What are the two ways the Master Policy can enable the PSM?

The **Master Policy** is like the **main rulebook** for the entire CyberArk system.

It can control PSM in **two different ways**.

## Method 1 — Enable PSM for Everyone (Global)

This means:

> **Every privileged account must go through PSM.**

Think of it like this:

```
User
  │
  ▼
PSM (Security Guard)
  │
  ▼
Target Server
```

No matter who logs in...

- Windows Server
    
- Linux Server
    
- Database
    
- Network Device
    

...everyone must first go through PSM.

This is the most secure option.

---

## Method 2 — Enable PSM by Exceptions

Instead of protecting **everything**, CyberArk says:

> "Only these specific accounts need PSM."

Example:

|Account|Use PSM?|
|---|---|
|Windows Admin|✅ Yes|
|Linux Root|❌ No|
|SQL Admin|✅ Yes|
|Test Account|❌ No|

Only selected accounts are forced through PSM.

---

## Simple Summary

```
Method 1

EVERY account
      │
      ▼
     PSM
      │
      ▼
 Target

----------------------------

Method 2

Windows Admin ─► PSM
SQL Admin ─────► PSM

Linux Root ───► Direct Login
Test User ────► Direct Login
```

---

# 2. How do you disable the PSM globally using the Master Policy dropdown interface?

Imagine the Master Policy has a giant ON/OFF switch.

Normally it looks like this:

```
PSM

Enabled
```

If you change the dropdown to:

```
Disabled
```

CyberArk says:

> "By default, nobody has to use PSM anymore."

You're **turning off the global rule**.

This **does not remove PSM from CyberArk**.

It only removes the rule that says:

> "Everyone must use PSM."

Now CyberArk waits to see whether any **exceptions** are configured.

Think of it like:

```
Before

Everyone → PSM

After

Everyone → Direct Login
(unless an exception says otherwise)
```

---

# 3. How does activating the PSM by exceptions work in practice regarding user access to target systems?

This is where the exception list becomes important.

Imagine a school.

Normally:

```
Every student
must wear a helmet.
```

Then the principal changes the rule.

Now:

```
Only these students wear helmets.
```

CyberArk works exactly the same way.

Suppose we have four accounts.

```
Windows Admin
Linux Root
Oracle DBA
Test Account
```

You enable PSM **only** for:

- Windows Admin
    
- Oracle DBA
    

Now when users connect:

```
Windows Admin
     │
     ▼
   PSM
     │
     ▼
 Server

--------------------

Oracle DBA
     │
     ▼
   PSM
     │
     ▼
 Database

--------------------

Linux Root
     │
     ▼
 Direct Login

--------------------

Test Account
     │
     ▼
 Direct Login
```

So the exception is simply a list saying:

> "These accounts must still go through PSM."

Everyone else connects normally.

---

## Why would a company do this?

Maybe they only want to record sessions for:

- Domain Admins
    
- Database Administrators
    
- Critical Production Servers
    

But not for:

- Test servers
    
- Lab machines
    
- Temporary accounts
    

This gives them flexibility.

---

# 4. What visual change happens to the "Connect" button once the PSM is disabled by default and enabled only by exception?

This is actually a very easy question.

Normally, if PSM is enabled globally, every logon account shows a:

```
[ Connect ]
```

button.

That button launches the session through PSM.

---

After you disable PSM globally...

Most accounts are **no longer allowed** to use PSM.

So CyberArk changes what you see.

For accounts **without** a PSM exception:

```
No Connect button
```

or the button is unavailable because those accounts are no longer configured to connect through PSM.

Only accounts that are specifically marked as **exceptions** continue to display the **Connect** button.

Example:

| Account       | PSM Exception? | Connect Button       |
| ------------- | -------------- | -------------------- |
| Windows Admin | ✅ Yes          | ✅ Visible            |
| SQL Admin     | ✅ Yes          | ✅ Visible            |
| Linux Root    | ❌ No           | ❌ Hidden/Unavailable |
| Test User     | ❌ No           | ❌ Hidden/Unavailable |

The Connect button becomes a quick visual clue that tells you:

> "This account is configured to connect through PSM."

---

# Beginner Analogy

Imagine an amusement park.

🎢 **PSM** = Security gate

👤 **Users** = Visitors

There are two ways the park can operate:

### Option 1: Everyone goes through security

```
Visitor
   │
   ▼
Security Gate
   │
   ▼
Ride
```

### Option 2: Only VIP visitors go through security

```
VIP Visitor
     │
     ▼
Security Gate
     │
     ▼
Ride

---------------------

Regular Visitor
      │
      ▼
Ride
```

The **Master Policy** decides which of these two rules the park follows.

---

## Key Takeaways

- **Master Policy** is the main rulebook for CyberArk.
    
- **PSM** is the secure gateway that records and controls privileged sessions.
    
- There are **two ways** to use PSM:
    
    1. **Globally** – every privileged connection goes through PSM.
        
    2. **By exceptions** – only selected accounts use PSM.
        
- Setting the Master Policy to **Disabled** removes the global requirement for PSM, allowing only explicitly configured exceptions to use it.
    
- When PSM is enabled only by exception, **only those exception accounts display the "Connect" button**; other accounts no longer show it because they are not configured to launch sessions through PSM.