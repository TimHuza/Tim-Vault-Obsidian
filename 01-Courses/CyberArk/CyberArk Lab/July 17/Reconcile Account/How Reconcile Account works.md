#cyberark-labs 


Let's imagine you are **12 years old** and you have a **robot (CyberArk)** that takes care of many computer passwords.

The robot normally works like this:

```
CyberArk Vault
      |
      |
      v
     CPM
      |
      |
      v
 Windows Server / Linux Server
```

The **CPM (Central Policy Manager)** is the CyberArk component that changes passwords.

But sometimes CPM has a problem:

> "The password I have saved does not work anymore!"

This is where the **Reconcile Account** helps.

---

# 1. First: What is happening without reconciliation?

Imagine CyberArk manages this account:

```
Account:
Windows Administrator

CyberArk Vault password:
OldPassword123
```

CyberArk thinks:

> "The Administrator password is OldPassword123."

But someone manually changed it:

```
Real server password:
NewPassword456
```

Now CyberArk tries to login:

```
Username:
Administrator

Password:
OldPassword123
```

The server says:

```
❌ Access Denied
Wrong Password
```

CyberArk says:

> "Oh no! My password is different from the real password."

This is called:

```
Password Out Of Sync
```

---

# 2. CyberArk asks the Reconcile Account for help

The Reconcile Account is like a **master key**.

Example:

Normal account:

```
Administrator
```

Problem:

```
❌ Password does not work
```

Reconcile account:

```
CyberArk_Reconcile_Admin
```

It has special permission:

```
Can change Administrator password
```

So CyberArk says:

> "I cannot enter as Administrator. I will use my emergency account."

---

# 3. CPM logs in using the Reconcile Account

The CPM does this:

```
CPM
 |
 |
 | Login using:
 |
 | CyberArk_Reconcile_Admin
 |
 v

Server
```

The server checks:

```
Username:
CyberArk_Reconcile_Admin

Password:
ReconcilePassword123
```

The server says:

```
✅ Welcome!
```

Now CPM is inside.

---

# 4. Reconcile Account changes the broken password

Now CPM tells the server:

> "Please change Administrator's password."

Like this:

```
Before:

Administrator
Password:
NewPassword456


After:

Administrator
Password:
Xy9#kLm77
```

The reconcile account had permission to do this.

---

# 5. CyberArk updates the Vault

The CPM tells the Vault:

```
The new password is:

Xy9#kLm77
```

The Vault updates:

```
Administrator
=
Xy9#kLm77
```

Now everything matches again.

---

# Complete Flow

The whole story:

```
                Password mismatch

CyberArk Vault
       |
       |
       v
      CPM
       |
       |
       v
 Try Administrator login
       |
       |
       v
      ❌ FAIL


       |
       |
       v

Use Reconcile Account

       |
       |
       v

Login as:
CyberArk_Reconcile_Admin

       |
       |
       v

Change Administrator password

       |
       |
       v

Save new password in Vault

       |
       |
       v

       ✅ Fixed
```

---

# Real-Life Example: House Keys 🏠

Imagine:

You have a house.

Your normal key:

```
Blue Key
```

CyberArk stores:

```
Blue Key = Password123
```

Someone changes the lock.

Now:

```
Blue Key ❌ does not work
```

But you have:

```
Master Key
```

The master key:

1. Opens the door
    
2. Changes the lock
    
3. Creates a new normal key
    

That is exactly what a **Reconcile Account** does.

---

# Who uses the Reconcile Account?

Usually:

```
CPM
 |
 |
 v
Reconcile Account
 |
 |
 v
Target System
```

A human administrator usually does **not** use it.

It is mainly for:

- Password mismatch problems
    
- Forgotten passwords
    
- Manual password changes
    
- Failed password rotations
    

---

# Reconcile Account vs Password Change

Many beginners confuse these.

## Normal Password Change

CyberArk knows the password:

```
Old password ✅
        |
        v
Change password
        |
        v
New password
```

---

## Password Reconciliation

CyberArk does NOT know the password:

```
Old password ❌
        |
        v
Use Reconcile Account
        |
        v
Fix password
```

---

# Easy memory trick 🧠

Remember:

```
CHANGE:
"I know the password. Make a new one."

RECONCILE:
"I don't know the password. Fix it for me."
```

So when you see **Reconcile Account** in CyberArk, think:

> "This is CyberArk's emergency backup account that CPM uses to repair broken password synchronization." ✅