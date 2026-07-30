#cyberark-labs 
[[Disaster Recovery Questions]]

# 🏥 First: What is Disaster Recovery (DR)?

Imagine your school has:

- 🏫 **Main School** = Primary Vault (`vault01`)
    
- 🏫 **Backup School** = DR Vault (`drvault01`)
    

Every day the backup school copies everything from the main school.

If the main school burns down (server failure), everyone immediately goes to the backup school.

That process is called **Failover**.

Later, after the main school is repaired, everyone moves back.

That is called **Failback**.

---

# Topic 1: Disaster Recovery Phases & Pre-Configurations

---

# 1. What are the two primary phases of testing Disaster Recovery?

There are **2 big phases**.

## Phase 1 — Failover

Primary Vault dies.

↓

DR Vault takes over.

```
Before

Primary Vault ✅
DR Vault (waiting)

        │
        ▼

Primary crashes

        │
        ▼

DR Vault becomes Primary
```

Purpose:

- Keep CyberArk running
    
- Users keep logging in
    
- Password management continues
    

---

## Phase 2 — Failback

Later...

Primary Vault is repaired.

Now we move everything back.

```
DR Vault (currently active)

      │

Copy newest data

      │

      ▼

Primary Vault becomes active again
```

Purpose:

- Return to the normal architecture.
    

---

# 2. What user account was manually created for failback?

CyberArk already has a built-in user:

```
DR
```

But the implementation team also created another account:

```
DR_Failback
```

Purpose:

This account helps copy all new data from the DR Vault back to the Primary Vault during the failback process.

Think of it like:

```
DR User
↓

Copies Primary → DR

----------------------

DR_Failback

Copies DR → Primary
```

Each account has a different job.

---

# 3. Why must you NEVER change the built-in DR user's password?

Because CyberArk expects that password.

Many DR services use it automatically.

If you change it:

```
Service

↓

Uses old password

↓

Cannot login

↓

Replication stops
```

Then:

❌ DR synchronization fails.

CyberArk documentation warns not to change it because many internal components depend on it.

Think of it like changing the key to the backup school without telling the teachers.

---

# 4. Why was automatic failover disabled during the course?

Because students were learning.

If automatic failover were enabled immediately:

Someone might accidentally stop the Primary Vault.

↓

The DR Vault immediately takes over.

↓

Everyone's lab changes.

↓

Chaos.

So the instructors disabled it until everyone understood how DR works.

Purpose:

- Safe learning
    
- No accidental failovers
    
- Easier troubleshooting
    

---

# Topic 2: Triggering and Monitoring Failover Replication

---

# 5. How do you enable the DR user?

In PVWA:

```
Administration

↓

User Provisioning

↓

Users

↓

DR

↓

Edit

↓

Uncheck "Disabled"

↓

Save
```

Now the DR user is active and can log in.

---

# 6. What is padr.ini?

Remember from the previous lesson:

```
padr.ini
```

is the instruction file for the Disaster Recovery service.

Think of it like:

```
Instruction Book

If Primary dies...

↓

Do this...

↓

Copy data...

↓

Start failover...
```

One important setting is:

```
EnableFailover=Yes
```

This tells CyberArk:

> "Yes, automatically switch to the DR Vault if the Primary Vault becomes unavailable."

If it says:

```
EnableFailover=No
```

CyberArk will **not** perform automatic failover.

---

# 7. How do you force a full replication?

Normally CyberArk copies only changes.

Example:

Yesterday:

```
100 accounts
```

Today:

```
101 accounts
```

It copies:

```
+1 account
```

A **full replication** copies **everything** again.

```
Primary Vault

↓

Copy ALL safes

↓

Copy ALL users

↓

Copy ALL passwords

↓

Copy ALL metadata

↓

DR Vault
```

The lab has you temporarily modify settings in `padr.ini` to force this full synchronization.

Purpose:

Ensure the DR Vault has a complete, fresh copy of the Primary Vault.

---

# 8. Why use Windows Services and padr_log.ps1?

The DR service runs in Windows.

You start or restart it using:

```
Services
```

Then you watch what happens using:

```
padr_log.ps1
```

Think of it like live subtitles.

```
Copying...

Copying...

Safe 1 copied...

Safe 2 copied...

Metadata copied...

Finished!
```

Instead of guessing, you can watch every step.

---

# 9. What success messages appear?

At the end you'll see messages showing:

- Metadata replication completed
    
- Replication completed successfully
    
- Informational status codes indicating the process finished without errors
    

These messages confirm the DR Vault is fully synchronized and ready if failover is needed.

---

# Topic 3: Executing Automatic Failover Tests

---

# 10. How do you perform a failover test?

The lab uses the:

```
Remote Control Client
```

to intentionally stop the Primary Vault service.

```
Primary Vault

↓

Stopped

↓

DR notices

↓

Automatic failover begins
```

This safely simulates a real disaster.

---

# 11. What happens behind the scenes?

The DR Vault keeps trying to contact the Primary Vault.

```
Hello?

...

Hello?

...

Hello?
```

No response.

It writes failed connection attempts into the logs.

After enough failures:

```
Primary unavailable

↓

Entering Failover Mode
```

The DR Vault decides the Primary is truly offline.

---

# 12. How do you know failover worked?

Open:

```
Windows Services
```

on:

```
drvault01
```

You'll see the Vault service running.

That means:

```
DR Vault

↓

Started Vault Engine

↓

Now serving users
```

The backup has officially become the active vault.

---

# 13. What is the Vault.ini automatic failover configuration?

Normally a service connects like this:

```
Vault = vault01
```

Problem:

If vault01 dies...

Everything breaks.

Instead:

```
Vault.ini

Primary = vault01

Secondary = drvault01
```

Now:

```
Try vault01

↓

Unavailable?

↓

Automatically use drvault01
```

Services like:

- PVWA
    
- PSM
    

can reconnect automatically without someone editing configuration files.

---

# 14. Which CyberArk component is NOT automatically configured?

The **CPM (Central Policy Manager)** is **not** configured for automatic failover in this architecture.

It requires additional planning because password changes and reconciliations must be carefully coordinated after a disaster.

---

# Topic 4: The Failback Process

---

# 15. What data must be handled before switching back?

While the DR Vault is active, users continue working.

New things happen:

- New passwords
    
- New safes
    
- New accounts
    
- New logs
    
- New audit records
    

All of that must be copied back.

Otherwise:

```
DR

Password changed

↓

Primary

Old password
```

Now the two vaults disagree.

---

# 16. How do you enable DR_Failback?

Using the classic:

```
PrivateArk Client

↓

Users

↓

DR_Failback

↓

Properties

↓

Uncheck Disabled

↓

Save
```

Now it can perform the reverse synchronization.

---

# 17. Why change FailoverMode?

Before receiving data, the repaired Primary Vault must behave as a **staging** system instead of acting like the active vault.

The lab has you update the `FailoverMode` setting and remove temporary logging/timestamp entries so it is ready to accept synchronized data from the DR Vault.

---

# 18. What changes appear in System Health?

The System Health dashboard shows that:

- The Primary Vault is available again.
    
- It is preparing or synchronizing instead of serving production traffic.
    
- The DR Vault is still the active production vault until failback finishes.
    

This lets you confirm the transition stage before switching roles.

---

# Topic 5: Finalizing Manual Failback

---

# 19. What does ActivateManualFailover do?

In the configuration file you enable:

```
ActivateManualFailover=Yes
```

This tells the Vault Disaster Recovery service:

> "When you start, perform the manual failback process."

It's a deliberate command rather than an automatic switch.

---

# 20. Why is manual failback so important?

Imagine this:

```
DR Vault

Newest passwords
```

Primary:

```
Old passwords
```

If you switch back immediately:

Users may receive outdated passwords.

Audit logs may be missing.

Password management may fail because the Primary doesn't have the newest information.

That's why CyberArk requires the proper failback sequence before returning production to the Primary Vault.

---

# 21. What happens when the DR service starts?

When `ActivateManualFailover` is enabled:

```
DR Service starts

↓

Reads configuration

↓

Begins failback process

↓

Synchronizes data

↓

Transfers control back to Primary
```

It follows the instructions automatically at startup.

---

# 22. How does drvault01 return to standby mode?

After the Primary Vault is fully active again:

```
Primary

✅ Active

↓

DR

Stops acting as Primary

↓

Returns to replication mode

↓

Waits for the next emergency
```

The DR Vault resumes its normal job of continuously copying changes from the Primary Vault.

---

# 23. Why disable the DR and DR_Failback accounts afterward?

Once testing is complete, you disable both accounts again.

Purpose:

- Reduce security risk.
    
- Prevent accidental use.
    
- Follow the principle of least privilege (accounts should only be active when needed).
    

Think of it like putting emergency keys back into a locked glass box—they're available for emergencies but not left lying around.

---

# 🎯 The Entire Disaster Recovery Story

```text
               NORMAL OPERATION

          Primary Vault (vault01)
                    │
          Copies changes continuously
                    │
                    ▼
           DR Vault (drvault01)

────────────────────────────────────

           PRIMARY SERVER FAILS

          Primary Vault ❌
                    │
       DR detects repeated failures
                    │
                    ▼
       Automatic Failover Starts
                    │
                    ▼
      DR Vault becomes Active Vault

────────────────────────────────────

        USERS KEEP WORKING ON DR

      Passwords continue changing
      New accounts are added
      Audit logs continue growing

────────────────────────────────────

      PRIMARY SERVER IS REPAIRED

Enable DR_Failback account
Prepare vault01 for synchronization
Copy all new data from DR → Primary

────────────────────────────────────

        MANUAL FAILBACK

ActivateManualFailover = Yes
Restart DR service
Synchronization completes

────────────────────────────────────

          BACK TO NORMAL

      Primary Vault ✅ Active
      DR Vault ✅ Standby
      Continuous replication resumes

Disable DR and DR_Failback accounts
```

This entire process ensures that even if the Primary Vault fails unexpectedly, CyberArk can continue operating with minimal downtime, and once the Primary is repaired, all changes made during the outage are safely synchronized back before normal operation resumes.