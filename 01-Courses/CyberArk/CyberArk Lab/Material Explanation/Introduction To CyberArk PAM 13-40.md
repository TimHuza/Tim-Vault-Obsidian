#cyberark-labs 


In this section of your lab, you are stepping into the role of a **system administrator** for a fake company called **Acme Corp**. Think of CyberArk as a **super-secure digital fortress** where a company keeps the "skeleton keys" (passwords) to its most important computers and systems.

Here is a breakdown of what you are doing in this part of the guide:

### 1. Setting Up Your Home Base

- **The Mission:** Your job is to take control of the company's most important passwords and keep them safe in the CyberArk Vault.
- **The Control Center:** You will do most of your work on a computer named **`comp01`**. In this lab, this server acts as your main workstation where you run all your tools.
- **Waking Up the Computers:** You start by turning on several "virtual" computers, like the **Vault** (the digital safe) and a **Domain Controller** (which handles the list of employees).

### 2. Getting to Know the Tools

In the first exercise, you practice using the different ways to "talk" to the CyberArk Vault:

- **Logging in as "Mike":** You log into your workstation using the name **Mike**, who is the head administrator in this story.
- **The PVWA (The Website):** You open a web browser to access the **Password Vault Web Access**. This is the main website where you can see all the digital keys you are allowed to use.
- **Using a Key (Connecting):** You find an account (like the one for a Linux computer) and click a **"Connect"** button. This lets you use that computer without ever seeing the actual password.
- **The Security Camera (PSM):** When you connect, a message pops up saying **"You are being recorded"**. This is a tool called the **PSM**; it’s like a security camera that records everything a person does while using a company secret so they can't do anything bad.

### 3. Managing the Secrets

Once you are inside the website, you learn how to handle the passwords themselves:

- **Seeing the Secret:** You learn how to use the "Classic" (older) part of the website to actually **show the secret password** on the screen if you really need to see it.
- **The Password Robot (CPM):** You practice telling a special "robot" tool called the **CPM** to **change a password immediately**. The robot creates a brand-new, long, and confusing password that nobody knows, which makes the computer extra safe.

### 4. Looking Under the Hood

Finally, you use a "heavy-duty" tool called the **PrivateArk Client**:

- **The Master Key:** You log in using a special built-in **Administrator** account to see things a normal user can't.
- **The Vault's Diary:** You open a folder (called a **Safe**) named **System** to find a file called **`italog.log`**. This file is like the Vault's **private diary**—it lists everything that has happened, like when the Vault started or if someone tried to log in.

By the time you finish this section, you will know how to log in, how to use secrets to get into other computers, and how to use the "robot" to keep those secrets fresh and safe.