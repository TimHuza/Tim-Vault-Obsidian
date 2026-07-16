#concepts 

# What is a central directory?

A **central directory** is simply **one place where a company stores information about all of its users and devices**.

Think of it as one giant address book.

Instead of every application having its own list of users, **everyone uses the same list**.

---

## Without a central directory

Imagine a company has three applications:

- CyberArk
    
- Email
    
- VPN
    

Each application stores its own users.

```text
CyberArk Database
-----------------
John
Sarah
Mike

Email Database
--------------
John
Sarah
Mike

VPN Database
------------
John
Sarah
Mike
```

Notice something?

The same users exist **three times**.

If John changes his password, the company has to update it in all three places.

That is inefficient and can lead to inconsistencies.

---

## With a central directory

Instead, the company creates one directory.

```text
             Central Directory

John
Sarah
Mike
Alice
Bob
```

Now every application asks the same directory.

```text
               Central Directory
                       ▲
          ┌────────────┼────────────┐
          │            │            │
          │            │            │
     CyberArk       Email         VPN
```

There is only **one source of truth**.

---

# What information is inside?

A central directory contains information like:

```text
John Smith

Username:
john

Password:
********

Email:
john@company.com

Department:
IT

Manager:
Mike

Groups:
IT Admins
CyberArk Users
VPN Users

Phone:
555-1234
```

It can also contain:

- Computers
    
- Servers
    
- Printers
    
- Security groups
    
- Organizational Units (OUs)
    
- Service accounts
    

So it stores much more than just usernames and passwords.

---

# How does it work?

Let's follow an example.

Suppose John wants to log in to CyberArk.

---

## Step 1

John types:

```text
Username:
john

Password:
*******
```

---

## Step 2

CyberArk receives the login.

```text
John

↓

CyberArk
```

CyberArk doesn't immediately know if John is a valid employee.

---

## Step 3

CyberArk asks the central directory.

```text
CyberArk
     │
     │ Is there a user named John?
     ▼
Central Directory
```

---

## Step 4

The directory searches its records.

```text
Searching...

John

Found!
```

---

## Step 5

The directory checks the password.

```text
Password correct?

Yes
```

---

## Step 6

The directory replies.

```text
Central Directory

↓

Yes

↓

CyberArk
```

CyberArk allows John to log in.

---

# Where is the central directory?

This is another excellent question.

The central directory is **not inside CyberArk**.

It usually lives on one or more dedicated servers in the company's network.

For example:

```text
                 Company Network

Employee PC
      │
      │
      ▼

CyberArk Server
      │
      │
      ▼

LDAP Server
```

The **LDAP server** is the computer that stores the directory.

---

For reliability, companies often have more than one LDAP server:

```text
            Company Network

            LDAP Server 1
                 ▲
                 │
Applications ────┤
                 │
                 ▼
            LDAP Server 2
```

If one server fails, another can continue providing directory services.

---

# Is the central directory a file?

No.

It is usually:

- a server running directory software, and
    
- a database containing directory information.
    

You can think of it like this:

```text
Computer
   │
   ├── Operating System
   │
   ├── LDAP Software
   │
   └── Directory Database
```

The LDAP software responds to requests such as:

> "Find John."

or

> "Is this password correct?"

---

# Is LDAP the central directory?

Not exactly.

This is a common point of confusion.

**LDAP is the language (protocol)** used to talk to the directory.

The **central directory** is the actual collection of user information stored on a directory server.

An analogy:

```text
Phone

↓

English Language

↓

Another Person
```

- The **person** = the directory (where the information lives).
    
- The **English language** = LDAP (how you communicate with it).
    

So:

- **Central directory** = the data and directory service.
    
- **LDAP** = the protocol applications use to query and authenticate against that directory.
    

---

# A real company example

Imagine a company with 2,000 employees.

The company has:

- Email
    
- VPN
    
- CyberArk
    
- Jira
    
- File Server
    
- Wi-Fi
    

Instead of each application storing employee accounts separately, they all connect to the company's central directory.

```text
                     Central Directory
                    (LDAP Directory)

                         ▲
        ┌────────┬───────┼────────┬────────┐
        │        │       │        │        │
     CyberArk  Email    VPN     Jira   File Server
```

When a new employee joins:

1. IT creates **one account** in the central directory.
    
2. All connected applications can use that account.
    

This is why it's called **central**—there is one shared place that all applications rely on for identity information.