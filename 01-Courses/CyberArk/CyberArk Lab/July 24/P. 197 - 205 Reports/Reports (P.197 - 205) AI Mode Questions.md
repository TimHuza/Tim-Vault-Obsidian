#cyberark-labs 
[[Reports questions]]


Think of CyberArk like a **high-security bank**:

- **Vault** = the bank safe where passwords are stored
    
- **PVWA** = the website where users interact with CyberArk
    
- **Auditor** = the person who checks security activity
    
- **Reports** = security camera summaries
    
- **EVD** = a tool that exports bank records for analysis
    

Let's go topic by topic.

---

# Topic 1: PVWA Modern Interface Reports

---

# 1. What is CyberArk’s rule regarding strict compartmentalization of information?

### Simple explanation:

CyberArk follows a security rule called:

> **Strict compartmentalization of information**

This means:

> **Users should only see information they are allowed to see.**

CyberArk does NOT allow everyone to generate every report.

Example:

Imagine a school:

- Principal can see everyone's grades
    
- Teacher can see only their class
    
- Student can see only their own grades
    

CyberArk works the same way.

---

Example:

User Tom:

```
Permissions:
✔ Safe: Windows_Admin
✔ View Accounts

Cannot see:
❌ Database Safe
❌ HR Safe
```

Tom can only generate reports about things he has permission to access.

---

Why?

Because reports can contain sensitive information:

- Account names
    
- User activity
    
- Server names
    
- Security events
    

If everyone could see everything:

```
Employee:
"Let me download all administrator accounts."
```

That would be dangerous.

---

# 2. What are the three groups reports are divided into?

When clicking:

```
Generate Report
```

Reports are divided into:

## 1. Operational Reports

Shows CyberArk health.

Examples:

- Password changes
    
- Password verification
    
- CPM activities
    

---

## 2. Audit / Compliance Reports

Shows:

- Who did something
    
- When they did it
    
- What they accessed
    

Example:

```
User:
Cindy

Action:
Retrieved Administrator password

Time:
10:30 AM
```

---

## 3. List Reports

Shows inventories.

Examples:

- List of accounts
    
- List of Safes
    
- List of users
    

---

# 3. Why is Cindy chosen to generate reports?

Cindy is chosen because she has the correct permissions.

Usually in labs:

Cindy represents an:

```
Auditor
```

or

```
Security Administrator
```

The Auditor role needs to:

- View activities
    
- Generate reports
    
- Investigate events
    

But Cindy does NOT need permission to change passwords.

---

Think:

A police officer can watch security cameras.

But they don't own the bank vault.

---

# 4. What filters are available for Privileged Accounts Inventory report?

Before generating the report, CyberArk allows filtering.

Common filters:

## Account properties:

- Account Name
    
- Username
    
- Address
    
- Platform
    

Example:

```
Show only:

Platform:
Windows Server

Safe:
Production

Account:
Administrator
```

---

## Status filters:

Examples:

- Active accounts
    
- Disabled accounts
    
- Pending accounts
    

---

## Ownership filters:

Examples:

- Safe owner
    
- Account owner
    

---

The purpose:

Instead of:

```
10,000 accounts
```

you get:

```
Only Windows Administrator accounts
```

---

# 5. How do you generate a report immediately?

Normally reports may run on a schedule.

Example:

```
Every Monday at 9 AM
```

But you want it now.

You click:

```
Run Now
```

or

```
Generate Now
```

depending on CyberArk version.

---

Meaning:

"CyberArk, don't wait for the schedule. Create it immediately."

---

# 6. How do you download completed report data?

After CyberArk finishes:

Go to:

```
Reports
 ↓
Completed Reports
 ↓
Download
```

The report downloads as:

```
CSV file
```

Example:

```
PrivilegedAccountsInventory.csv
```

CSV means:

Comma Separated Values.

It looks like a spreadsheet.

Example:

```
Account,Platform,Safe

Administrator,Windows,Servers
root,Linux,Unix
```

---

# 7. What tool opens the downloaded file?

Usually:

```
Microsoft Excel
```

opens CSV files.

If Windows asks:

"How should this file be saved?"

Choose:

```
CSV UTF-8 (Comma delimited)
```

or:

```
CSV (Comma delimited)
```

depending on version.

---

---

# Topic 2: Export Vault Data (EVD) Utility

---

# 1. What is EVD?

EVD means:

> Export Vault Data

It is a CyberArk utility used to export Vault information.

Think:

Vault:

```
Millions of security events
```

EVD:

```
Take selected information
and export it
```

---

Why?

Because companies sometimes use other tools:

Examples:

- Splunk
    
- SIEM systems
    
- Excel analysis
    
- Reporting platforms
    

---

Example:

CyberArk:

```
User logged in
Password changed
Session recorded
```

↓

EVD

↓

CSV file

↓

Splunk dashboard

---

# 2. What files does EVD export?

EVD can export data into:

```
CSV files
```

and

```
XML files
```

These formats can be read by other programs.

---

# 3. How do you enable the built-in Auditor user?

Normally:

You could use:

```
PrivateArk Client
```

But modern PVWA allows it.

Go:

```
PVWA

Administration

Users

Auditor
```

Enable the user.

---

Think:

The Auditor account exists but is sleeping.

You wake it up.

---

# 4. How do you assign a password to Auditor?

Go:

```
PVWA

Users

Auditor

Authentication Settings
```

Set:

```
Password Authentication
```

Create password.

Save.

---

Now Auditor can log in.

---

# Topic 3: Credential Files & Hardening

---

# 1. What terminal window must be used?

You must use:

```
Command Prompt
```

or

```
PowerShell
```

with:

```
Administrator privileges
```

Why?

Because creating credential files requires system permissions.

---

# 2. Why secure the credential file?

The credential file contains authentication information.

Example:

```
auditor.cred
```

It is like a key.

If someone steals it:

They may access CyberArk.

---

Like:

Password = house key

Credential file = master key

---

CreateCredFile.exe allows administrators to:

- Encrypt the file
    
- Restrict which machine can use it
    
- Restrict which application can use it
    
- Add password protection
    

---

Example:

Only:

```
Server01

Application:
ExportVaultData.exe

User:
Auditor
```

can use it.

---

# 3. How to configure Vault.ini?

Open:

```
Vault.ini
```

using:

```
Notepad
```

Find:

```
Address=
```

Set Vault IP address.

Example:

```
Address=192.168.1.10
```

Meaning:

"The Vault server is here."

---

# 4. CreateCredFile.exe command

The command looks like:

```
CreateCredFile.exe auditor.cred
```

with parameters.

Example:

```
CreateCredFile.exe auditor.cred /Username Auditor /AppType ExportVaultData /OSUser
```

The parameters define:

- Who can use it
    
- Which application can use it
    
- Security restrictions
    

---

# 5. Alternative interactive method?

Instead of typing all security options:

Run:

```
CreateCredFile.exe auditor.cred
```

only.

Then CyberArk asks questions:

Example:

```
Enter username:
Enter password:
Restrict application:
Restrict machine:
```

You answer interactively.

---

# 6. Why does "Disable wait for DR synchronization before allowing password change" create warning?

CyberArk sees this setting as risky.

Why?

Because DR means:

```
Disaster Recovery Vault
```

Normally:

Primary Vault

↓

Synchronizes

↓

DR Vault

---

If you allow password changes before synchronization:

Primary:

```
Password = ABC123
```

DR:

```
Password = OLD123
```

They are different.

CyberArk warns:

"Are you sure?"

---

In the lab:

It is expected.

You should:

- Read warning
    
- Continue
    
- Do not worry
    

because it is only a testing environment.

---

# Topic 4: Running Data Exports

---

# 1. How do you execute ExportVaultData?

You run:

```
ExportVaultData.exe
```

with configuration files.

Example:

```
ExportVaultData.exe /IniFile Export.ini
```

It reads instructions and creates reports.

---

# 2. What are the four backslash parameters?

The `\` parameters define:

---

## 1. Initialization file

Tells EVD:

"Read this configuration."

Example:

```
\ExportVaultData.ini
```

---

## 2. Target

Where to connect.

Example:

```
\Vault
```

---

## 3. Logging window

Defines:

How much history to export.

Example:

```
\30
```

means:

Last 30 days.

---

## 4. Output file

Where to save results.

Example:

```
\Activities.csv
```

---

# 3. Generated activity report name and history period

The generated report is:

```
Activities.log
```

(or Activities.csv depending on configuration)

It collects:

```
Previous 7 days
```

of Vault activity.

---

# Final Memory Cheat Sheet 🧠

|Topic|Remember|
|---|---|
|Reports|CyberArk activity summaries|
|Operational Reports|"Is CyberArk working?"|
|Audit Reports|"Who did what?"|
|List Reports|"What exists?"|
|EVD|Export Vault information|
|CSV/XML|Export formats|
|Auditor|Security investigator|
|Credential file|Secure key to access CyberArk|
|Vault.ini|GPS location of Vault|
|CreateCredFile.exe|Creates protected credential files|
|ExportVaultData.exe|Generates external reports|

---

A good way to remember the whole flow:

```
CyberArk Vault
      |
      |
      v
Reports
      |
      |
      v
EVD Export
      |
      |
      v
CSV/XML Files
      |
      |
      v
Excel / SIEM / Audit Tools
```

CyberArk stores the truth → Reports show the truth → EVD exports the truth.