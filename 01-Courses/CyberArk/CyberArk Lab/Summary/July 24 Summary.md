#cyberark-labs 


This summary covers the vital systems that act as the security guards, cleanup crews, and emergency responders for the CyberArk "digital fortress," based on the provided sources.

### **1. The Cleanup Crew (PSM Session Terminator)**

Imagine you are at a **public library** using a computer. When you finish, a **cleanup robot** checks to make sure you closed every program and logged out of every website so no one else can see your secrets.

- **What it does:** If an administrator accidentally closes a window by clicking the "X" instead of logging out, programs might stay running in the background.
- **Why it's important:** It automatically closes these leftover programs to save the server's memory and ensure that sensitive passwords aren't left behind. It's like a **housekeeper** in a hotel who locks the door and cleans the room for the next guest.

### **2. The Activity Summary (Reports)**

Reports are like a **library summary** that tells the librarian exactly who borrowed which books. They are the "report card" for the security system.

- **Operational Reports:** These answer **"Is everything working?"** by showing if passwords were changed successfully.
- **Audit / Compliance Reports:** These act like a **security camera**, answering **"Who did what?"** so you can see exactly who logged into which server.
- **List Reports:** These are simple **inventories**, like a class roster, that list all the Safes or users you have.
- **Export Vault Data (EVD):** This is a tool used to take these records out of CyberArk so they can be read by other programs like Excel or Splunk.

### **3. The Safety Snapshots (Backup and Restore)**

This is how you protect against accidents, like someone deleting a file they still need.

- **PAReplicate (The Camera):** This tool takes a **"snapshot"** or a backup copy of all your Safes and accounts.
- **PARestore (The Time Machine):** If a Safe is accidentally removed, this tool uses those snapshots to bring it back to life.
- **The Players:** You use two special users for this: the **Backup** user (who takes the pictures) and the **Operator** user (who runs the time machine).
- **DPAPI Machine Protection:** This is a Windows feature that "locks" secret files so they **only work on one specific computer**. If a thief steals the backup file, it's useless because it won't open on their laptop.

### **4. The Spare School (Disaster Recovery)**

While a backup is just a copy of files, **Disaster Recovery (DR)** is a whole second "spare" Vault server ready to take over if the main one fails.

- **Failover (The Automatic Switch):** If the Primary Vault "falls over" or crashes, the system automatically **switches everyone to the DR Vault**, much like a phone switching from Wi-Fi to mobile data.
- **Failback (The Return):** Once the main Vault is fixed, you perform a **Failback** to move all the new information from the backup server back to the main one.
- **The Manual (`padr.ini`):** This is the **instruction book** for the DR service.

### **5. Important Configuration Files**

- **Vault.ini (The GPS):** This file tells all the components exactly where the Vault is located on the network so they don't get lost.
- **tsparm.ini (The Rule Book):** This notebook of settings tells CyberArk services exactly how to behave.