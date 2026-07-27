#cyberark-labs 


![[options-parameters.png]]

# 📄 Version Information

## What is it?

Shows what version of CyberArk you're running.

Example:

```text
CyberArk Version
14.2
```

---

### Why do we need it?

Suppose you call CyberArk Support.

The first thing they'll ask is:

> "What version are you using?"

Just like Windows 10 vs Windows 11.

---

## Beginner Summary

> Shows the CyberArk software version.

---

# ⚙️ General

## What is it?

General settings that affect the whole CyberArk system.

Examples:

- Company name
    
- Default settings
    
- Timeouts
    

Think of it like the Settings app on your phone.

---

## Beginner Summary

> Basic settings used by the whole CyberArk system.

---

# 📥 Accounts Feed

## What is it?

Automatically imports account information from outside sources.

Instead of adding accounts one by one...

CyberArk can receive a list.

```text
CSV File
    │
    ▼
CyberArk
```

---

### Why?

Imagine adding 5,000 servers manually...

Not fun.

---

## Beginner Summary

> Automatically imports account information.

---

# 👤 Users

Controls CyberArk users.

Examples:

- Create users
    
- Delete users
    
- Login settings
    

---

Think:

```text
Who can log in?
```

---

## Beginner Summary

> Manages CyberArk users.

---

# 🤖 CPM Names

CPM = **Central Policy Manager**

CyberArk may have multiple CPM servers.

Example:

```text
CPM-01

CPM-02

CPM-Test
```

This section manages their names.

---

## Beginner Summary

> Lists the CPM servers CyberArk knows about.

---

# 🔒 Search Properties

Controls:

> What users can search for.

Example:

Search by:

✔ Username

✔ Address

✔ Platform

✔ Safe

---

## Beginner Summary

> Controls how searching works.

---

# 🌐 Internal Properties

Settings used internally by CyberArk.

Most administrators rarely change these.

Think:

Hidden engine settings.

---

## Beginner Summary

> Internal CyberArk settings.

---

# 📚 LDAP Search

LDAP is usually Active Directory.

CyberArk asks:

> "Can I find this user in Active Directory?"

```text
CyberArk
     │
     ▼
Active Directory
```

---

## Beginner Summary

> Controls how CyberArk searches Active Directory.

---

# 🔍 Search Results

Controls what appears after a search.

Example:

Instead of:

```text
Username
```

You can show:

```text
Username

Platform

Safe

Address
```

---

## Beginner Summary

> Controls what search results look like.

---

# 👤 Account Name Pattern

Creates naming rules.

Example:

Instead of random names:

```text
Admin01
```

CyberArk can require:

```text
SERVER-Administrator
```

---

## Beginner Summary

> Creates naming rules for accounts.

---

# 📊 Usage Name Pattern

Similar idea.

Controls naming for usage information.

Mostly for consistency.

---

## Beginner Summary

> Naming rules for usage records.

---

# 📝 Account Descriptor Properties

Extra information about an account.

Example:

```text
Owner

Department

Location
```

Like labels on a folder.

---

## Beginner Summary

> Extra information stored about accounts.

---

# 📁 File Descriptor Properties

Extra information for attached files.

---

## Beginner Summary

> Information about attached files.

---

# 📋 File Display Columns

Choose which columns appear.

Example:

```text
Name

Owner

Date

Size
```

---

## Beginner Summary

> Controls what columns users see.

---

# 📈 Statistics

CyberArk numbers.

Example:

- Number of users
    
- Number of accounts
    
- Number of Safes
    

---

## Beginner Summary

> Shows CyberArk statistics.

---

# 📊 Chart Categories

Controls graphs and dashboards.

---

## Beginner Summary

> Controls dashboard charts.

---

# 🌍 Web Charts

Charts shown inside PVWA.

---

## Beginner Summary

> Graphs displayed in the web interface.

---

# 🔑 Authentication Methods

Controls how users log in.

Examples:

✔ LDAP

✔ Radius

✔ SAML

✔ CyberArk Password

---

## Beginner Summary

> Controls login methods.

---

# 🛡 Default Safe Authorizations

When a Safe is created...

CyberArk automatically gives default permissions.

Like:

```text
Safe Owner

Can Add Accounts

Can Delete Accounts
```

---

## Beginner Summary

> Default permissions for new Safes.

---

# 🎫 Ticketing Systems

Integrates with:

- ServiceNow
    
- Jira
    
- Remedy
    

CyberArk can require a ticket number.

---

## Beginner Summary

> Connects CyberArk with help desk systems.

---

# 🔌 Connection Components

Very important!

These tell CyberArk:

> "How do I connect?"

Example:

- RDP
    
- SSH
    
- SQL
    

---

## Beginner Summary

> Instructions for connecting to target systems.

---

# 🖥 Privileged Session Management UI

Controls what users see during PSM sessions.

---

## Beginner Summary

> Settings for the PSM user interface.

---

# 🖥 Privileged Session Management

Controls PSM itself.

Examples:

Recording

Session timeout

Clipboard

HTML5

---

## Beginner Summary

> Main settings for PSM.

---

# 📄 Reports

Controls reporting.

Example:

Who logged in?

Who changed passwords?

---

## Beginner Summary

> Creates reports.

---

# 🚫 Access Restriction

Creates rules.

Example:

Only allow login:

Monday-Friday

8 AM - 5 PM

---

## Beginner Summary

> Restricts who can access CyberArk.

---

# 📜 Logging

CyberArk diary.

Everything gets written down.

```text
Tim logged in

Password changed

Session started

Session ended
```

---

## Beginner Summary

> Records everything that happens.

---

# ⚡ Caching

Stores temporary information.

Makes CyberArk faster.

Like keeping your favorite app already open.

---

## Beginner Summary

> Improves performance.

---

# 🔗 Configuration References

Links one setting to another.

CyberArk uses these internally.

---

## Beginner Summary

> References shared configuration settings.

---

# ✅ Privileged Account Request

Controls password requests.

Example:

User requests password

↓

Manager approves

↓

CyberArk releases password

---

## Beginner Summary

> Settings for password requests and approvals.

---

# 🎨 Applications UI Preferences

Controls how application pages look.

---

## Beginner Summary

> Appearance settings for application pages.

---

# ⚙ Applications

Settings for applications integrated with CyberArk.

---

## Beginner Summary

> Controls application integrations.

---

# 🔧 Setup Configuration

General installation settings.

Usually configured during installation.

---

## Beginner Summary

> Basic setup configuration.

---

# 👤 Accounts UI Preferences

Changes how account pages look.

---

## Beginner Summary

> Appearance settings for account pages.

---

# 👥 Users Collections

Groups of users.

Instead of:

500 users individually...

Create one collection.

---

## Beginner Summary

> Organizes users into groups.

---

# ❓ Web Help

Help documentation.

Like clicking:

```text
?
```

---

## Beginner Summary

> Built-in help pages.

---

# 📦 Application Assemblies

Software components CyberArk uses internally.

Think of them as Lego pieces that make the application work.

---

## Beginner Summary

> Internal application components.

---

# 📨 Message Queue Connection

CyberArk services communicate with each other.

Imagine sending letters.

```text
CPM
 │
 ▼
Message Queue
 │
 ▼
PVWA
```

---

## Beginner Summary

> Lets CyberArk components communicate.

---

# 📤 Bulk Operations

Import or update many accounts at once.

Example:

Instead of:

1 account...

Do:

1,000 accounts.

---

## Beginner Summary

> Performs large operations all at once.

---

# 🔌 API Throttling

Limits how many API requests can happen.

Imagine a store.

Only 20 people allowed inside.

Not 5,000.

---

## Beginner Summary

> Prevents the API from becoming overloaded.

---

# 🔍 Audit Filters

Chooses which events get recorded.

Instead of recording everything...

Record only important actions.

---

## Beginner Summary

> Filters audit logs.

---

# 🚩 Feature Flags

Turns features ON or OFF.

Example:

```text
New Dashboard

ON

Old Dashboard

OFF
```

---

## Beginner Summary

> Enables or disables specific features.

---

# 🌉 ADBridge Settings

Controls CyberArk's integration with Active Directory.

CyberArk uses these settings to communicate with AD for user authentication, synchronization, and other directory-related tasks.

---

## Beginner Summary

> Settings for connecting CyberArk with Active Directory.

---

# 🎯 The Big Picture

```text
                    CYBERARK
                        │
 ┌─────────────────────────────────────────────┐
 │                                             │
 │  👤 Users        → Who can log in          │
 │  🔑 Authentication → How they log in       │
 │  🗄 EPV          → Stores passwords         │
 │  🤖 CPM          → Changes passwords        │
 │  🖥 PSM          → Records sessions         │
 │  🔌 Components   → Connect to servers       │
 │  📋 Reports      → What happened?           │
 │  📜 Logging      → Audit everything         │
 │  🎫 Ticketing    → ServiceNow/Jira          │
 │  🌐 LDAP         → Active Directory         │
 │  🚫 Restrictions → Security rules           │
 │  📦 Bulk Ops     → Manage many accounts     │
 │  ⚡ Cache        → Improve performance      │
 │                                             │
 └─────────────────────────────────────────────┘
```

## 💡 As a CyberArk beginner, focus on these first

You don't need to master every configuration immediately. These are the ones you'll encounter most often in labs:

1. **Users** – Who can use CyberArk.
    
2. **Authentication Methods** – How users log in.
    
3. **Connection Components** – How CyberArk connects to Windows, Linux, databases, etc.
    
4. **Privileged Session Management (PSM)** – How sessions are secured and recorded.
    
5. **Default Safe Authorizations** – Who gets what permissions in a Safe.
    
6. **Ticketing Systems** – Requiring a ServiceNow/Jira ticket before access.
    
7. **Logging** – Recording everything for auditing.
    
8. **Bulk Operations** – Importing or updating many accounts efficiently.
    

These eight sections form the foundation of most CyberArk administration tasks, and understanding them will make the rest of the configuration options much easier to learn.