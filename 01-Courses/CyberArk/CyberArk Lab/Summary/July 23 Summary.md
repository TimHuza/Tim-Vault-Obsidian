#cyberark-labs 


This summary covers the core components and security controls used to manage privileged access, focusing on the concepts from your latest lab exercises (pages 171–192).

### **1. The Heart of CyberArk: The Vault (EPV)**

The **Enterprise Password Vault (EPV)** is the center of the CyberArk system.

- **Purpose:** It acts like a giant, high-security bank vault. Instead of money, it stores the company's most sensitive "skeleton keys," such as Windows Administrator passwords, Linux Root passwords, and database secrets.
- **Why it's used:** In a large company with thousands of servers, keeping passwords in a spreadsheet is dangerous. The Vault ensures that passwords are never written down and don't need to be memorized by humans.

### **2. The Gatekeeper: Privileged Session Manager (PSM)**

The **PSM** is the secure gateway that sits between a user and a target server. It has two main jobs:

- **Isolation:** It prevents a user's computer from ever touching the target server directly, which stops malware from spreading.
- **Recording:** It acts like a security camera, recording every click and command typed during a session.

### **3. Controlling Access: The "Master Policy"**

The **Master Policy** is the main rulebook for CyberArk. It decides how people are allowed to connect:

- **Global Rule (ON):** Every single privileged account must go through the PSM.
- **By Exception:** You turn the global rule "OFF" and then create a specific list of "important" accounts (like Domain Admins or Production Servers) that still require the PSM.
- **The Visual Clue:** If an account is not allowed to use the PSM, its **"Connect" button** will disappear or turn grey.

### **4. Connection Methods**

CyberArk offers several ways to log into a server depending on what the user needs:

- **Transparent Connection:** This is when CyberArk logs in for you. You never see, touch, or type the password; it is "hidden" behind the scenes.
- **HTML5 Gateway:** This lets you connect to a server directly inside your **web browser** (like Chrome or Edge). You don't need to install any special Remote Desktop software on your computer.
- **PSM for Windows/SSH:** This allows experts to use their favorite tools (like **mstsc** for Windows or **PowerShell** for Linux) while still routing the session through the secure PSM proxy.
- **Ad-Hoc Connection:** This allows you to use the PSM to securely connect to a server that isn't even saved in the Vault yet (unmanaged accounts).

### **5. Secure File Transfers (Drag-and-Drop)**

When using a PSM session, moving files between your computer and a server is strictly controlled.

- **How it works:** You can't just move files anywhere. CyberArk creates a special **Mapped Drive (usually the Z: drive)**.
- **The Control:** CyberArk can be set to allow uploads, block downloads, or monitor everything to ensure no one is stealing data or uploading viruses.

### **6. The "Beginner's Foundation" for Configuration**

There are dozens of settings in CyberArk, but for a beginner, these **eight areas** are the most important to understand first:

1. **Users:** Managing who can log into CyberArk.
2. **Authentication:** Choosing how they log in (e.g., LDAP/Active Directory).
3. **Connection Components:** The instructions for _how_ to connect (RDP, SSH, SQL).
4. **PSM Settings:** Controlling how sessions are recorded and isolated.
5. **Default Safe Authorizations:** Setting standard permissions for new Safes.
6. **Ticketing Systems:** Requiring a help desk ticket (like ServiceNow) before someone can access a server.
7. **Logging:** The "diary" that records every action for auditors.
8. **Bulk Operations:** Tools for adding or updating hundreds of accounts at once.