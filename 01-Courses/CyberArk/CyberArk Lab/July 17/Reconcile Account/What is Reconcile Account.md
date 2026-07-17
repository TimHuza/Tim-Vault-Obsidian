#cyberark-labs 


Imagine you are **12 years old** and you have a **school locker**.

Your locker has a password, but one day something goes wrong:

- You forgot the password.
    
- Someone changed the password without telling you.
    
- The password in your notebook is different from the real locker password.
    

Now you have a problem: **you cannot open your own locker.**

A **Reconcile Account** in CyberArk is like having a **special master key** that can fix the problem.

---

# What is a Reconcile Account?

A **Reconcile Account** is a special privileged account that CyberArk uses to **fix (synchronize) passwords when CyberArk loses control of an account password**.

In simple words:

> A reconcile account is an account that CyberArk uses to log in and change the password of another account when the password is unknown or incorrect.

---

# Why do we need Reconcile Accounts?

CyberArk manages thousands of privileged accounts:

Examples:

- Windows Administrator accounts
    
- Domain Admin accounts
    
- Database administrator accounts
    
- Linux root accounts
    
- Service accounts
    

CyberArk automatically changes passwords using the **CPM (Central Policy Manager)**.

The normal flow:

```
CyberArk Vault
        |
        |
        v
       CPM
        |
        |
        v
 Target Server
```

Example:

CyberArk says:

> "Every 30 days, change the Administrator password."

CPM connects to the server:

```
Username: Administrator
Old Password: Password123
New Password: Xy#72kLm!
```

The password changes successfully.

CyberArk updates the Vault:

```
Vault:
Administrator
Password = Xy#72kLm!
```

Everything is happy. ✅

---

# But what if something goes wrong?

Imagine this happens:

CyberArk thinks:

```
Vault password:
Admin123
```

But someone manually changed the server password:

```
Actual server password:
NewPassword456
```

Now CyberArk tries:

```
Login:
Administrator
Password:
Admin123
```

The server replies:

```
❌ Wrong password
```

CyberArk is now "locked out".

This is called:

> **Password out of sync**

---

# How does Reconcile Account fix it?

The reconcile account comes to help.

Example:

You have:

## Account CyberArk manages

```
Account:
Administrator

Password:
Unknown to CyberArk
```

## Reconcile Account

```
Account:
Reconcile_Admin

Password:
ReconcilePassword123
```

The reconcile account has permission to change Administrator's password.

The process:

```
                 CyberArk Vault
                       |
                       |
                       v
                    CPM
                       |
                       |
          "I cannot login as Administrator"
                       |
                       v
              Use Reconcile Account
                       |
                       v
              Login as Reconcile_Admin
                       |
                       v
        Change Administrator password
                       |
                       v
          Update CyberArk Vault
```

After that:

```
Vault password:
NewCorrectPassword!
```

Everything is synchronized again. ✅

---

# Simple Example

Imagine:

You manage a Minecraft server.

You have:

```
Admin Account:
Steve

Password:
12345
```

CyberArk stores:

```
Steve = 12345
```

Someone changes it:

```
Steve = ABC789
```

CyberArk tries:

```
Steve + 12345
```

Server says:

```
NO!
```

Now CyberArk uses:

```
Reconcile Account:
SuperAdmin
```

SuperAdmin changes:

```
Steve password:
XYZ999
```

CyberArk saves:

```
Steve = XYZ999
```

Problem solved.

---

# Reconcile Account vs Regular Account

|Account|Purpose|
|---|---|
|Regular privileged account|The account CyberArk manages|
|Reconcile account|Emergency account used to fix passwords|
|CPM account|The account that performs password management|
|Vault account|Stores the secrets|

---

# Where do you configure Reconcile Account?

Usually inside:

```
CyberArk PVWA
        |
        |
        v
Account Properties
        |
        |
        v
Authentication
        |
        |
        v
Reconcile Account
```

You assign:

```
Reconcile Account:
DOMAIN\CyberArk_Reconcile
```

---

# Real Company Example

A company has:

```
Domain Administrator
        |
        |
        v
CyberArk manages password
```

They create:

```
DOMAIN\CyberArk_Reconcile
```

This account has:

```
Permission:
Change Domain Admin password
```

If Domain Admin password becomes wrong:

```
CPM
 |
 |
 v
Cannot login
 |
 |
 v
Uses Reconcile Account
 |
 |
 v
Fixes password
```

---

# Important CyberArk Terms

### Password Change

CyberArk knows the password and changes it.

Example:

```
Old:
Password123

New:
K8#f92Lm
```

---

### Password Verification

CyberArk checks:

"Does the password in Vault still work?"

Example:

```
Vault says:
Admin = ABC123

Testing...

Login successful ✅
```

---

### Password Reconciliation

CyberArk says:

"I cannot login. I need another account to fix the password."

Example:

```
Normal account ❌

Reconcile account ✅

Fix password
```

---

# Easy way to remember

Think:

```
VERIFY = Check the password

CHANGE = Update the password

RECONCILE = Fix a broken password connection
```

or:

```
Verification:
"Is my key working?"

Change:
"Make me a new key"

Reconcile:
"I lost my key, use the master key to make a new one"
```

---

In a CyberArk lab, when you see **Reconcile Account**, think:

> "This is CyberArk's emergency repair account that CPM uses when it cannot access an account because the password is wrong or out of sync." ✅