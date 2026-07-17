#cyberark-labs 


![[automatic-password-management-params.png]]
# Think of CyberArk as a Robot 🤖

Imagine you have a robot named **CyberBot**.

Your job is to tell CyberBot how to take care of the passwords.

You give CyberBot instructions like:

- "Change the password every month."
    
- "Make sure the password actually works."
    
- "If something goes wrong, tell me."
    
- "Create strong passwords."
    

The sections below are the different instruction pages for CyberBot.

---

# 1. General

## What is it?

These are the **basic settings** for automatic password management.

Think of it as the robot's "main settings."

It answers questions like:

- Is automatic password management enabled?
    
- Should CyberArk manage this account automatically?
    
- What are the general rules?
    

---

## Example

Imagine your robot.

Before it can clean your room, you first have to turn it ON.

General is like this button:

```
Robot
--------
Power: ON ✅
```

If it's OFF...

CyberArk won't automatically manage passwords.

---

## Why do we need it?

Because some accounts should be managed automatically...

...and some shouldn't.

---

# 2. Privileged Account Management

## What is it?

This section tells CyberArk **when and how** it should manage privileged accounts.

It controls the overall password management policy.

For example:

- Should passwords expire?
    
- When should CyberArk change them?
    
- Should CyberArk verify them?
    

---

## Think of it like...

A calendar for your chores.

Mom says:

> "Every Saturday clean your room."

CyberArk says:

> "Every 30 days change this password."

---

## Why do we need it?

To make sure passwords don't stay the same forever.

Old passwords are less secure.

---

# 3. CPM Plug-in

This is one of the coolest concepts in CyberArk.

## First...

What is CPM?

CPM stands for:

> **Central Policy Manager**

Think of CPM as the worker robot that actually changes passwords.

---

But...

How does the robot know how to log into Windows?

Or Linux?

Or Oracle?

It needs instructions.

Those instructions are called a **CPM Plug-in**.

---

## Example

Imagine CyberBot wants to change a Windows password.

It follows the Windows instruction book.

```
Windows Guide

1. Log in
2. Open Users
3. Change password
4. Save
```

Now imagine Linux.

The steps are completely different.

CyberBot uses a different guide.

---

Each platform has its own CPM Plug-in.

---

## Think of it like...

A chef.

The chef can cook:

🍕 Pizza

🍔 Burger

🍝 Pasta

Each recipe is different.

The chef is the same.

The recipe changes.

CPM = Chef

Plug-in = Recipe

---

## Why do we need it?

Because every system changes passwords differently.

---

# 4. Password Change

This section tells CyberArk:

> **How should I change the password?**

---

Questions include:

- Which account should perform the change?
    
- Which CPM Plug-in should be used?
    
- What order should the steps happen?
    

---

## Example

CyberArk does this:

```
Old Password

↓

Login

↓

Change Password

↓

Save New Password

↓

Store New Password
```

---

Think of it like changing the combination on your locker.

---

# 5. Password Verification

Changing the password isn't enough.

CyberArk must ask:

> "Did it actually work?"

---

Example

CyberArk changes:

```
Dog123
```

to

```
Blue$Tree91
```

But...

What if something failed?

CyberArk logs in using:

```
Blue$Tree91
```

If login works:

✅ Password verified

If login fails:

❌ Something went wrong.

---

Think of it like...

After changing your bike lock combination...

You test it.

If it opens...

Everything is good.

---

## Why do we need it?

Without verification...

CyberArk might save the wrong password.

Nobody could log in anymore!

---

# 6. Password Reconciliation

This one sounds scary.

It's actually very simple.

---

Imagine your little brother secretly changes the tablet password.

CyberArk doesn't know.

Now CyberArk's password is wrong.

---

CyberArk tries to log in.

```
CyberArk thinks:

Password = Apple123
```

Reality:

```
Password = Banana456
```

Oops.

---

CyberArk can't log in anymore.

---

A **Reconcile Account** comes to the rescue.

It has enough permissions to reset the password.

CyberArk uses it to set a new password.

Now everything matches again.

---

Think of it like...

Your teacher has a master key.

If students lose their locker key...

The teacher opens it anyway.

The teacher's key is like the Reconcile Account.

---

## Why do we need it?

Because sometimes people change passwords outside CyberArk.

Reconciliation fixes that.

---

# 7. Notifications

CyberArk can send messages.

For example:

📧

"Password change failed."

or

"Password successfully changed."

or

"Verification failed."

---

Think of it like...

Your washing machine beeping:

> "Laundry is done!"

CyberArk also tells you when something important happens.

---

## Why do we need it?

Admins don't have to watch CyberArk all day.

CyberArk tells them if something needs attention.

---

# 8. Generate Password

This tells CyberArk:

> **What should the new password look like?**

---

Example

Should it have:

✅ Uppercase letters

```
A B C
```

✅ Lowercase letters

```
a b c
```

✅ Numbers

```
1 2 3
```

✅ Symbols

```
! @ #
```

How long?

```
8 characters?

12?

20?

32?
```

---

CyberArk builds strong passwords automatically.

Example:

```
Tiger!94Blue#Moon7
```

instead of

```
password123
```

---

Think of it like...

A LEGO instruction book.

You choose the pieces.

CyberArk builds the password.

---

# 9. Additional Policy Settings

These are extra rules that don't fit neatly into the other sections.

They let you customize how password management behaves for special situations.

Examples might include:

- Special timing rules.
    
- Advanced password management options.
    
- Platform-specific settings.
    

---

Think of it like...

The "Advanced Settings" menu in a video game.

Most players never touch it.

But experienced users can fine-tune things.

---

# Putting It All Together

Imagine it's time to change a Windows Administrator password.

CyberArk follows these steps:

```
General
│
├── Is automatic management enabled?
│
▼
Privileged Account Management
│
├── Is it time to change the password?
│
▼
CPM Plug-in
│
├── Use the Windows instructions.
│
▼
Password Change
│
├── Change the password.
│
▼
Password Verification
│
├── Test the new password.
│
▼
Password Reconciliation
│
├── If verification fails because someone changed the password manually,
│   use the Reconcile Account to fix it.
│
▼
Generate Password
│
├── Create a strong new password.
│
▼
Notifications
│
├── Tell the administrator whether everything succeeded or failed.
│
▼
Additional Policy Settings
│
└── Apply any extra special rules.
```

---

# Easy Way to Remember

|Section|Simple Question|Think of it Like|
|---|---|---|
|**General**|Is automatic password management turned on?|Robot power switch|
|**Privileged Account Management**|When and how should passwords be managed?|Chore calendar|
|**CPM Plug-in**|Which instructions should the robot follow?|Recipe book|
|**Password Change**|How do we change the password?|Changing a locker combination|
|**Password Verification**|Did the new password actually work?|Testing the new key|
|**Password Reconciliation**|How do we recover if CyberArk's password is wrong?|Teacher's master key|
|**Notifications**|Should CyberArk tell someone what happened?|Phone notification|
|**Generate Password**|What should the new password look like?|LEGO instructions for building a strong password|
|**Additional Policy Settings**|Are there any extra special rules?|Advanced settings menu|

## One Thing to Remember

Many beginners think **CPM changes passwords by itself**. That's not quite true.

A better way to think about it is:

- **The Platform** = the rulebook 📖
    
- **The CPM** = the worker 🤖
    
- **The CPM Plug-in** = the instruction manual for a specific system 📚
    

The Platform tells the CPM **what** to do, and the CPM Plug-in tells it **how** to do it for Windows, Linux, databases, or any other supported system. That's how CyberArk can manage thousands of different account types automatically.