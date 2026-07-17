#cyberark-labs 


![[dbparm.ini file.png|697]]

`dbparm.ini` is one of the **most important configuration files** in CyberArk. Think of it as the **Vault's settings menu**. It tells the CyberArk Digital Vault how it should behave when it starts.

---

# Think of it like a video game

Imagine you're making a Minecraft server.

Before your friends join, you configure things like:

- Maximum players
    
- Server port
    
- Autosave
    
- Difficulty
    
- Allowed file types
    
- Backups
    
- Security
    

CyberArk does exactly the same thing.

Instead of configuring a game server, you're configuring a **CyberArk Vault**.

---

# The structure

Your file has sections:

```ini
[MAIN]
...
[BACKUP]
...
[CRYPTO]
...
[SYSLOG]
...
```

Each section contains settings (variables).

A variable looks like this:

```ini
TasksCount=20
```

- Left side = variable name
    
- Right side = value
    

CyberArk reads these values every time the Vault starts.

---

# \[MAIN\]

This is the biggest section.

It contains the main Vault settings.

---

# TasksCount

```ini
TasksCount=20
```

## What is it?

The number of worker tasks the Vault can use.

Think of them as workers inside the Vault.

---

## How does it work?

Imagine a restaurant.

One worker serves food slowly.

Twenty workers can serve many customers at once.

CyberArk works the same way.

More tasks =  
more things can happen simultaneously.

---

## Purpose

To make the Vault faster.

---

# DateFormat

```ini
DateFormat=DD.MM.YY
```

## What?

How dates are displayed.

Example:

```
15.07.26
```

instead of

```
07/15/2026
```

---

## How?

Whenever CyberArk prints a date, it follows this format.

---

## Purpose

Keeps all dates consistent.

---

# TimeFormat

```ini
TimeFormat=HH:MM:SS
```

## What?

How time is displayed.

Example

```
14:35:09
```

---

## How?

CyberArk uses this format in logs and reports.

---

## Purpose

Makes timestamps easy to read.

---

# ResidentDelay

```ini
ResidentDelay=10
```

## What?

How often background tasks "wake up."

---

## Imagine

A security guard checks every hallway every 10 seconds.

That's ResidentDelay.

---

## Purpose

Controls background checking frequency.

---

# VaultCommunicationProtocol

```ini
VaultCommunicationProtocol=Casos
```

## What?

The language computers use to talk to the Vault.

---

## Imagine

People speak English.

Computers speak protocols.

CASOS is CyberArk's own communication protocol.

---

## Purpose

Lets CyberArk components communicate.

---

# BasePort

```ini
BasePort=1858
```

## What?

The network door number the Vault listens on.

---

## Imagine

A building has many doors.

Door **1858** is where CyberArk waits.

---

## Purpose

Allows clients to connect.

---

# LogRetention

```ini
LogRetention=7
```

## What?

How many days logs are kept.

---

## How?

Older logs are deleted automatically.

---

## Purpose

Saves disk space.

---

# LockTimeout

```ini
LockTimeout=30
```

## What?

How long something stays locked.

---

## Imagine

You borrow a library book.

Nobody else can use it until you return it.

CyberArk temporarily locks objects the same way.

---

## Purpose

Prevents two users changing the same object.

---

# DaysForAutoClear

```ini
DaysForAutoClear=30
```

## What?

How many days before old information is cleaned up.

---

## Purpose

Keeps the Vault clean.

---

# DaysForPicturesDistribution

```ini
DaysForPicturesDistribution=Never
```

## What?

Controls distribution of user pictures.

Usually not important.

---

## Purpose

Manages user picture synchronization.

---

# ClockSyncTolerance

```ini
ClockSyncTolerance=600
```

## What?

Maximum allowed clock difference.

---

## Imagine

Your watch says

```
10:00
```

Mine says

```
10:09
```

CyberArk says

"That's close enough."

---

## Purpose

Prevents problems caused by small clock differences.

---

# TraceArchiveMaxSize

```ini
TraceArchiveMaxSize=5120
```

## What?

Maximum size of trace (debug) files.

---

## Purpose

Prevents trace logs from filling the disk.

---

# VaultEventNotifications

Very long line.

## What?

Which Vault events send notifications.

Example:

- New request
    
- Request approved
    
- Request rejected
    
- Request deleted
    

---

## Imagine

A teacher gets notified when:

- homework is submitted
    
- homework is graded
    
- homework is deleted
    

CyberArk does the same.

---

## Purpose

Keeps administrators informed.

---

# RecoveryPubKey

```ini
RecoveryPubKey=...
```

## What?

Public recovery key.

---

## How?

If disaster happens, CyberArk uses recovery keys.

Think of them as emergency keys.

---

## Purpose

Disaster recovery.

---

# ServerKey

```ini
ServerKey=...
```

## What?

Private server key.

---

## Imagine

A secret key to a safe.

Only the Vault should have it.

---

## Purpose

Encryption and authentication.

---

# StagingAreaDirectory

```ini
StagingAreaDirectory=C:\PrivateArk\Safes\...
```

## What?

Temporary working folder.

---

## Imagine

A kitchen counter before food is served.

---

## Purpose

Temporary storage.

---

# EntropyFile

```ini
EntropyFile=...
```

## What?

Randomness file.

---

## Imagine

Rolling dice thousands of times.

The random numbers help create strong encryption.

---

## Purpose

Improves encryption security.

---

# DatabaseConnectionPasswordFile

```ini
DatabaseConnectionPasswordFile=...
```

## What?

Stores password used by the Vault internally.

---

## Purpose

Keeps passwords out of plain text.

---

# ServerCertificateFile

```ini
ServerCertificateFile=...
```

## What?

The Vault's digital ID card.

---

## Imagine

Like your school ID.

It proves who you are.

---

## Purpose

Secure encrypted communication.

---

# ServerPrivateKey

```ini
ServerPrivateKey=...
```

## What?

Secret key paired with the certificate.

---

## Purpose

Used during encrypted communication.

---

# AllowedVirusSafeFileTypes

```ini
AllowedVirusSafeFileTypes=DOC,PDF,XLS,...
```

## What?

Files CyberArk considers safe.

---

## Purpose

Prevents dangerous file uploads.

---

# AutoClearSafeHistory

```ini
AutoClearSafeHistory=Yes
```

## What?

Automatically remove old Safe history.

---

## Purpose

Keeps history manageable.

---

# AutoClearUserHistory

```ini
AutoClearUserHistory=Yes
```

## What?

Automatically remove old user history.

---

## Purpose

Database cleanup.

---

# AutoSyncExternalObjects

```ini
AutoSyncExternalObjects=Yes
```

## What?

Automatically synchronize with external systems like LDAP or Active Directory.

---

## Purpose

Keeps users and groups updated.

---

# DebugLevel

```ini
DebugLevel=P(1),PERF(1,2)
```

## What?

How much debugging information CyberArk records.

---

## Purpose

Helps troubleshoot problems.

---

# VaultId

```ini
VaultId=...
```

## What?

Unique ID of the Vault.

---

## Imagine

Like a person's fingerprint.

No two Vaults should share it.

---

## Purpose

Uniquely identifies the Vault.

---

# DefaultTimeout

```ini
DefaultTimeout=30
```

## What?

Default waiting time before giving up.

---

## Purpose

Prevents operations from waiting forever.

---

# PooledSocketTimeout

```ini
PooledSocketTimeout=600
```

## What?

How long network connections stay open.

---

## Purpose

Improves performance by reusing connections.

---

# RecoveryPrvKey

```ini
RecoveryPrvKey=...
```

## What?

Private recovery key.

---

## Purpose

Used during Vault recovery.

---

# EmergencyStationIP

```ini
EmergencyStationIP=10.0.10.1
```

## What?

IP address of the emergency recovery computer.

---

## Purpose

Allows disaster recovery.

---

# EnablePredefinedUsers

```ini
EnablePredefinedUsers=ALL
```

## What?

Enables built-in CyberArk accounts.

---

## Purpose

Allows default administrative users to exist.

---

# ExternalAuthenticationMode

```ini
ExternalAuthenticationMode=...
```

## What?

Controls authentication using external systems.

Examples:

- LDAP
    
- Active Directory
    

---

## Purpose

Allows users to log in with company accounts.

---

# AutomaticallyAddBuiltInGroups

```ini
AutomaticallyAddBuiltInGroups=...
```

## What?

Automatically creates CyberArk built-in groups.

---

## Purpose

Saves administrator setup time.

---

# LicenseUsageAlertLevel

```ini
LicenseUsageAlertLevel=85,90,99
```

## What?

Percentage thresholds for license usage alerts.

---

## Imagine

If your parking lot is:

- 85% full → warning
    
- 90% full → stronger warning
    
- 99% full → almost full
    

---

## Purpose

Warn administrators before licenses run out.

---

# MaxTasksAllocation

Very long line.

## What?

Limits how many worker tasks each CyberArk service can use.

---

## Purpose

Prevents one service from using all resources.

---

# ComponentNotificationThreshold

## What?

How long CyberArk waits before warning that a component hasn't responded.

---

## Purpose

Detects slow or failed components.

---

# UserLockoutPeriodInMinutes

```ini
UserLockoutPeriodInMinutes=1
```

## What?

How long a locked account stays locked.

---

## Purpose

Protects against repeated failed logins.

---

# MaskUserIssuesMessages

```ini
MaskUserIssuesMessages=No
```

## What?

Whether detailed error messages are hidden from users.

---

## Purpose

Improves security by revealing less information.

---

# TerminatedMDBErrorCodes

```ini
TerminatedMDBErrorCodes=2003
```

## What?

Database error codes that CyberArk treats as fatal.

---

## Purpose

Proper error handling.

---

# MinSupportedClientVersion

```ini
MinSupportedClientVersion=11.5.0.0
```

## What?

Oldest CyberArk client version allowed.

---

## Purpose

Blocks outdated clients.

---

# MaxConcurrentUsersByClientID

```ini
MaxConcurrentUsersByClientID=...
```

## What?

Limits how many users each client type can connect simultaneously.

---

## Purpose

Prevents one client from consuming all available connections.

---

# \[BACKUP\]

## BackupKey

```ini
BackupKey=...
```

### What?

Encryption key for backups.

### How?

Every backup is encrypted with this key.

### Purpose

Keeps backup files secure.

---

# \[CRYPTO\]

## SymCipherAlg

```ini
SymCipherAlg=AES-256
```

### What?

Symmetric encryption algorithm.

### How?

CyberArk encrypts stored data using AES-256.

### Purpose

Protects Vault data.

---

## AsymCipherAlg

```ini
AsymCipherAlg=RSA-2048
```

### What?

Asymmetric encryption algorithm.

### How?

Uses a public key and a private key for secure communication and key exchange.

### Purpose

Securely exchanges encryption keys and verifies identities.

---

# \[SYSLOG\]

## UseLegacySyslogFormat

```ini
UseLegacySyslogFormat=Yes
```

### What?

Whether to use the older Syslog message format.

### Purpose

Allows CyberArk to work with older logging systems that expect the legacy format.

---

## An easy way to remember `dbparm.ini`

Think of the CyberArk Vault as a **high-security bank**:

- **Ports** are the **doors** people use to enter.
    
- **Keys and certificates** are the **master keys and employee ID cards**.
    
- **Encryption settings** are the **vault's giant steel walls** that protect valuables.
    
- **Timeouts** are **security guards** deciding how long to wait before taking action.
    
- **Logs** are the **security camera recordings**.
    
- **Tasks** are the **employees** doing work inside the bank.
    
- **Backup settings** are the **emergency copies** of everything important.
    
- **Authentication settings** are the **reception desk** checking everyone's identity before letting them in.
    

Keeping this analogy in mind makes `dbparm.ini` much easier to understand: it's essentially the **control panel that tells the CyberArk Vault how to run, communicate, protect itself, and recover from problems**.