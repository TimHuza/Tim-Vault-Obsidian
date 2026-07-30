#cyberark-labs 
[[Disaster Recovery Questions]]

# 1. What is PADR?

**PADR = Privileged Account Disaster Recovery**

Think of PADR as an **emergency backup plan** for CyberArk.

## Imagine this...

You have your favorite video game saved on your computer.

One day:

- 💥 Your computer breaks.
    
- 😨 You can't access your save file.
    

Luckily...

You also saved a copy on another computer.

You simply load the backup and continue playing.

CyberArk does exactly the same thing.

---

## What happens in CyberArk?

Normally, everything is stored in the **Digital Vault**.

```
Users
   │
   ▼
+----------------------+
|      Main Vault      |
| Passwords            |
| Safes                |
| Policies             |
+----------------------+
```

But what if something bad happens?

- Server crashes
    
- Hard drive fails
    
- Power outage
    
- Fire
    
- Flood
    
- Someone accidentally deletes something
    

Without a backup...

```
❌ Everything is gone.
```

That's very dangerous because companies could lose thousands of important passwords.

---

## PADR solves this problem

PADR continuously copies the Vault to another server.

```
           Copy

Main Vault -----------> Disaster Recovery Vault
     (Primary)              (Backup)
```

Now there are **two copies**.

If one dies...

the other one is still safe.

---

## How PADR Works

### Step 1

Users connect to the Main Vault.

```
User
   │
   ▼
Main Vault
```

---

### Step 2

PADR copies everything.

```
Main Vault
     │
     │ Copy
     ▼
DR Vault
```

This includes

- passwords
    
- safes
    
- users
    
- policies
    
- audit logs
    

Everything important.

---

### Step 3

Disaster happens.

```
💥 Main Vault crashes
```

---

### Step 4

The backup Vault already has a copy.

```
Main Vault ❌

DR Vault ✅
```

The company can continue working using the backup.

---

## Why is PADR Important?

Imagine a hospital.

CyberArk stores passwords for

- servers
    
- databases
    
- medical equipment
    

If the Vault disappears...

Doctors might not be able to access important systems.

PADR prevents that.

---

## Purpose of PADR

Its purpose is to:

- protect the Vault
    
- make a backup
    
- recover after disasters
    
- reduce downtime
    
- prevent password loss
    

---

## Simple Diagram

```
                Normal Operation

            +----------------+
            |  Main Vault    |
            +----------------+
                    │
          PADR copies data
                    │
                    ▼
            +----------------+
            | DR Vault       |
            +----------------+
```

---

# 2. What is Enable Failover?

Now let's talk about **Failover**.

---

## Imagine this...

You're watching YouTube.

Suddenly...

Your Wi-Fi stops working.

Your phone automatically switches to mobile data.

You don't have to do anything.

```
Wi-Fi ❌

↓

Mobile Data ✅
```

That's called **failover**.

Something stopped working...

Another system automatically takes over.

---

CyberArk works the same way.

Normally everyone connects here:

```
Users
   │
   ▼
Main Vault
```

But...

```
💥 Main Vault crashes
```

If **Failover is enabled**, CyberArk automatically switches to the backup Vault.

```
Before

Users
   │
   ▼
Main Vault


After Crash

Users
   │
   ▼
DR Vault
```

Users can keep working.

---

## If Enable Failover = No

```
Main Vault crashes

↓

Nobody can connect.

❌ Login fails
❌ Password requests fail
❌ CPM cannot manage passwords
```

Everything stops until someone fixes the Vault.

---

## If Enable Failover = Yes

```
Main Vault crashes

↓

CyberArk switches to DR Vault.

↓

Everyone keeps working.
```

Much better!

---

## Why Do We Need Enable Failover?

Because companies cannot afford to stop working.

Imagine:

- Bank
    
- Hospital
    
- Airport
    
- Government
    

If CyberArk stops...

Thousands of employees might not be able to log in.

Failover keeps everything running.

---

## Simple Example

Without Failover

```
Main Vault

💥 Crash

↓

Everything stops.
```

---

With Failover

```
Main Vault

💥 Crash

↓

Automatically switches

↓

DR Vault

↓

Business continues.
```

---

# How PADR and Enable Failover Work Together

Think of it like having **two schools**.

🏫 School A (Main Vault)

🏫 School B (Backup Vault)

Every day, School B copies all the homework and books from School A (this is **PADR**).

If School A suddenly closes because of a storm, everyone automatically goes to School B without losing their work (this is **Enable Failover**).

```
            PADR
(Main Vault) =====copies=====> (DR Vault)

        💥 Crash

             │
             ▼

      Enable Failover

             │
             ▼

Users automatically use the DR Vault
```

---

# Easy Way to Remember

|Term|Think of...|Purpose|
|---|---|---|
|**PADR**|Making a backup copy of your game save|Protects the Vault by copying its data to a Disaster Recovery Vault|
|**Enable Failover**|Your phone switching from Wi-Fi to mobile data|Automatically switches users to the backup Vault if the main Vault fails|

### 🧠 Memory Trick

- **PADR = Protect and Duplicate** (it **copies** the Vault to a backup location).
    
- **Failover = Fall Over → Switch Over** (if the main Vault "falls over," CyberArk **switches** to the backup Vault automatically).
    

So in simple terms:

- **PADR creates and keeps the backup up to date.**
    
- **Enable Failover tells CyberArk to automatically use that backup if the main Vault becomes unavailable.**