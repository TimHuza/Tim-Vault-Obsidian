#cyberark

![[10-lifecycle-of-cyber-attack.png|522]]
This diagram is one of the most important concepts in CyberArk. The main idea is:

> **Attackers don't just want to break into a company—they want privileged accounts (administrator accounts).** Once they have those, they can control almost everything.

Let's go through the image **step by step** as if we're watching a real cyber attack happen.

---

# Step 1. The attacker starts outside (or inside)

On the left side of the image you see two possibilities:

### External Threats

This is a hacker on the Internet.

```
Internet
    ↓
 Hacker
```

Example:

Someone sitting in another country tries to hack your company's VPN or website.

---

### Internal Threats

This is someone who already has access.

For example:

- an employee
    
- a contractor
    
- someone whose laptop was infected
    

They already have **some** access.

Think of it like this:

External threat

> "I'm outside the building trying to get in."

Internal threat

> "I'm already inside the building."

---

# Step 2. Perimeter Compromise

The image says:

> **Perimeter Compromise**

The **network perimeter** is basically the company's front door.

Imagine a company building.

```
Outside
---------
 Front Door
---------
Inside Office
```

The attacker must somehow get through that front door.

How?

For example:

- phishing email
    
- stolen VPN password
    
- software vulnerability
    
- malware
    

Now the attacker has entered the network.

---

# Step 3. Existing Access

Sometimes the attacker doesn't even need to hack in.

They already have a normal user account.

Example:

Employee account

```
tim@company.com
Password: ********
```

This account is **not** administrator.

It is just a regular employee account.

The attacker now wants something much more valuable...

---

# Step 4. Escalate Privileges ⭐

This is the **big blue arrow** in the picture.

This is the most important part.

The attacker wants to become:

- Local Administrator
    
- Domain Administrator
    
- Root
    
- Privileged User
    

Imagine this:

Regular employee

```
Can read emails
Can use Word
```

Administrator

```
Can install software
Can change passwords
Can control servers
Can disable antivirus
```

See the difference?

CyberArk exists largely to stop attackers from reaching this point.

---

# Real example

The attacker steals:

```
John's password
```

John is just an accountant.

Not very useful.

But then the attacker discovers:

```
John knows the local admin password.
```

Or:

John's computer has cached administrator credentials.

Now the attacker becomes administrator.

This is called

> **Privilege Escalation**

---

# Step 5. Move Laterally

Now look at the circle.

It says:

> Move Laterally

Imagine a hotel.

You broke into Room 101.

Instead of stealing only from Room 101...

you start opening every other room.

```
Room 101
    ↓
Room 102
    ↓
Room 103
    ↓
Room 104
```

In cybersecurity:

Computer A

↓

Computer B

↓

Database Server

↓

File Server

↓

Domain Controller

This is **Lateral Movement**.

Earlier you asked about lateral movement.

This is exactly where it happens.

---

# Step 6. Perform Reconnaissance

While moving around...

The attacker looks for valuable information.

This is called:

> Reconnaissance

Think of a burglar inside a house.

Instead of immediately stealing...

he first walks around.

He checks:

- Where is the safe?
    
- Where are the cameras?
    
- Which room has jewelry?
    

Attackers do exactly the same.

They ask questions like:

- What servers exist?
    
- Who is the Domain Admin?
    
- Where is the database?
    
- What privileged accounts exist?
    
- Which computer has sensitive data?
    

They gather information before attacking further.

---

# Step 7. Repeat

Notice the circle.

```
Recon
     ↓
Move
     ↓
Recon
     ↓
Move
```

Attackers don't do this once.

They repeat it.

Computer 1

↓

Computer 2

↓

Computer 3

↓

Server

↓

Domain Controller

Each time they gain more knowledge and access.

---

# Step 8. Credential Theft

On the right side of the image it says:

> Credential Theft

Credentials mean:

- usernames
    
- passwords
    
- SSH keys
    
- Kerberos tickets
    
- tokens
    

The attacker keeps stealing credentials.

For example:

```
User password

↓

Server password

↓

Administrator password

↓

Domain Admin password
```

The better the credentials...

the more powerful the attacker becomes.

---

# Step 9. Privilege Escalation Again

After stealing new credentials...

The attacker becomes even more powerful.

Example:

```
User

↓

Local Admin

↓

Server Admin

↓

Domain Admin
```

This keeps happening.

---

# Step 10. Exfiltrate Data

Near the bottom right it says:

> Exfiltrate Data

This simply means:

> **Stealing company data and sending it outside the company.**

For example:

The attacker copies

- customer information
    
- payroll
    
- source code
    
- financial records
    

and uploads them to their own server.

Imagine stealing documents from an office and carrying them outside in a backpack.

---

# Step 11. Disrupt Business

Finally...

The attacker damages the company.

Examples:

- ransomware
    
- deleting servers
    
- shutting down production
    
- encrypting files
    
- deleting backups
    

Now the company cannot work.

---

# Why is privilege in the center?

Look at the title:

> **Privilege is at the Center of the Attack Lifecycle**

This is exactly what CyberArk wants you to understand.

Imagine this timeline:

```
Enter network
      ↓
Become Administrator
      ↓
Move everywhere
      ↓
Steal passwords
      ↓
Steal data
      ↓
Destroy systems
```

Notice something?

Everything after the first step becomes much easier **because the attacker gained privileged access**.

Without administrator privileges:

❌ Can't install malware easily.

❌ Can't access sensitive servers.

❌ Can't dump passwords.

❌ Can't move across the network easily.

❌ Can't disable security tools.

With administrator privileges:

✅ Full control.

---

# Where does CyberArk help?

CyberArk focuses on protecting **privileged accounts** because those accounts are the attacker's primary goal.

Here's how different CyberArk components fit into this attack lifecycle:

|Attack Step|What the attacker does|How CyberArk helps|
|---|---|---|
|Initial access|Gets into the network|Not CyberArk's main focus (other security tools often handle this)|
|Credential theft|Tries to steal administrator passwords|**CPM** regularly changes privileged passwords, reducing the value of stolen credentials.|
|Privilege escalation|Tries to become an administrator|**PVWA** and the **Digital Vault** tightly control access to privileged credentials.|
|Lateral movement|Uses privileged accounts to access more systems|**PSM** brokers privileged sessions so users don't need to know the actual passwords, making credential theft much harder.|
|Reconnaissance & suspicious activity|Moves around looking for targets|**PTA** monitors privileged activity and detects unusual behavior such as abnormal logins or lateral movement patterns.|
|Data theft / disruption|Uses privileged access to steal or damage systems|CyberArk can limit, monitor, and audit privileged sessions, helping reduce the attacker's ability to misuse administrator accounts and providing evidence for incident response.|

---

## A simple story that ties it all together

Imagine a thief wants to rob a bank.

1. 🚪 He gets inside the building (**Perimeter Compromise**).
    
2. 👤 He steals an employee's badge (**Existing Access**).
    
3. 🔑 He finds the manager's master key (**Privilege Escalation**).
    
4. 🚶 With the master key, he walks into every room (**Lateral Movement**).
    
5. 👀 He looks for the vault (**Reconnaissance**).
    
6. 💰 He opens the vault and takes the money (**Exfiltrate Data**).
    
7. 💥 Before leaving, he destroys security cameras and locks everyone out (**Disrupt Business**).
    

The **master key** is the equivalent of a **privileged account**. That is why CyberArk is built around protecting privileged credentials—if attackers never get the "master key," it's much harder for them to progress through the rest of the attack lifecycle.