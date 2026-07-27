#cyberark-labs 

# What is a PSM Session Terminator?

Imagine you are at a **public library**.

The librarian gives you a special computer to use.

When you're done, the librarian doesn't just tell you to leave. They also make sure:

- You logged out of every website.
    
- You closed every program.
    
- Nobody can continue using your session.
    

That is exactly what a **PSM Session Terminator** does.

---

# First, what is a PSM Session?

Remember:

```
User
   │
   ▼
CyberArk PSM
   │
   ▼
Target Server
```

The user never connects directly to the server.

Instead:

1. User opens a session.
    
2. PSM connects to the server.
    
3. Everything is recorded.
    
4. When finished, the session ends.
    

Now comes the important part...

---

# What if the session doesn't close correctly?

Imagine the administrator accidentally closes Remote Desktop like this:

❌ Clicks the X button.

or

The network disconnects.

or

Their laptop crashes.

The Windows session on the server may still be running.

That is bad because:

- programs stay open
    
- passwords remain in memory
    
- someone else could reconnect
    
- resources are wasted
    

CyberArk doesn't want that.

---

# This is where the Session Terminator comes in

The **PSM Session Terminator** is like a **cleanup robot**.

When the session ends, it checks:

> "Did everything actually close?"

If not...

it closes everything automatically.

---

## Think of it like this

```
Administrator
      │
      ▼
Connects through PSM
      │
      ▼
Uses Remote Desktop
      │
      ▼
Administrator leaves
      │
      ▼
PSM Session Terminator wakes up
      │
      ▼
Closes programs
Logs off Windows
Ends session
Deletes temporary files
```

Everything is cleaned up.

---

# Why do we need it?

Imagine 100 administrators use CyberArk every day.

If nobody cleaned up after themselves...

```
Server

Session 1  (still open)
Session 2  (still open)
Session 3  (still open)
Session 4  (still open)
Session 5  (still open)
```

Eventually:

- memory fills up
    
- CPU usage increases
    
- security becomes weaker
    
- servers slow down
    

The Session Terminator prevents this.

---

# What does it terminate?

It can end things like:

✅ Windows logon sessions

✅ Remote Desktop sessions

✅ Applications started during the session

Examples:

```
mstsc.exe
powershell.exe
cmd.exe
notepad.exe
mmc.exe
Server Manager
```

If they were left running...

the Session Terminator closes them.

---

# Simple Example

### Step 1

Tom connects to a Windows Server.

```
Tom
   │
   ▼
PSM
   │
   ▼
Windows Server
```

---

### Step 2

Tom opens:

```
PowerShell

Server Manager

Command Prompt
```

Everything works normally.

---

### Step 3

Tom finishes and closes Remote Desktop.

But...

PowerShell is still running.

```
PowerShell
   Running...
```

CyberArk notices this.

---

### Step 4

The Session Terminator starts.

It says:

```
Close PowerShell

Close Command Prompt

Log off Windows

End Session
```

Now everything is clean.

---

# Why is this important?

Without a Session Terminator:

❌ Programs keep running.

❌ User sessions stay logged in.

❌ Sensitive information may remain in memory.

❌ Someone might reconnect to an existing session.

With a Session Terminator:

✅ Sessions are fully closed.

✅ Programs stop running.

✅ Resources are freed.

✅ Security is improved.

---

# Easy analogy

Imagine visiting a hotel room.

You leave.

Would you want the room to stay unlocked forever?

Of course not!

A housekeeper comes and:

- locks the door
    
- throws away the garbage
    
- changes the sheets
    
- gets the room ready for the next guest
    

The **PSM Session Terminator** is like the **housekeeper** for CyberArk sessions.

---

# Beginner Summary

|Question|Answer|
|---|---|
|What is a PSM Session Terminator?|A CyberArk feature that automatically cleans up and ends privileged sessions after users finish.|
|Why do we need it?|To prevent leftover sessions, improve security, and free server resources.|
|What does it do?|Logs users off, closes applications, ends Remote Desktop sessions, and cleans temporary session data.|
|When does it run?|After a PSM session ends or if a session is abandoned unexpectedly.|

## Easy way to remember

> **PSM lets an administrator safely enter a server.**  
> **The PSM Session Terminator makes sure they truly leave and nothing is left behind.**

Think of it as the **cleanup crew** that comes in after every privileged session to make the server safe and ready for the next administrator.