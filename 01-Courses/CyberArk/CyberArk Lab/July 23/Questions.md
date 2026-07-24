#cyberark-labs 

**Topic 1: Privileged Session Management & Platform Exceptions**

- **What** is "classic PSM" according to the guide? _(From page 171)_
- **How** do you add an exception to a specific platform (like _Lin Ssh 30_) using the PVWA classic interface? _(From page 171)_
- **What** specific Privileged Access Workflow option must you **NOT** disable when removing workflow exceptions? _(From page 171)_
- **What** are the two ways the Master Policy can enable the PSM? _(From page 172)_
- **How** do you disable the PSM globally using the Master Policy dropdown interface? _(From pages 172-173)_
- **How** does activating the PSM by exceptions work in practice regarding user access to target systems? _(From page 173)_
- **What** visual change happens to the "Connect" button for logon accounts once the PSM is disabled by default and enabled only by exception? _(From page 175)_

---

**Topic 2: HTML5 Gateway**

- **What** is the PSM HTML5 Gateway, and **what** primary requirement does it eliminate from the end user's machine? _(From page 176)_
- **How** does the HTML5 Gateway work to securely deliver the session to the end user (specify the protocol and port number)? _(From page 176)_
- **How** do you enable the HTML5 Gateway parameter for a configured PSM Server within the PVWA options? _(From page 177)_
- **How** does a user initiate an HTML5 connection from the ACCOUNTS page, and **what** must they select in the connection pop-up? _(From page 177)_
- **How** do you enable the functionality to toggle between an RDP file and an HTML5 Gateway connection for a non-default connection component like _PSM-WinSCP_? _(From page 178)_
- **How** do you enable the drive mapping feature in the PVWA parameters, and **what** values must you enter? _(From page 179)_
- **How** does a user transfer a file from their local workstation _to_ the remote machine using the HTML5 Gateway browser window? _(From page 180)_
- **How** does a user transfer a file in the opposite direction, from the remote machine _back to_ their local workstation? _(From page 182)_

---

**Topic 3: PSM Ad-Hoc Connection**

- **What** is a PSM Ad-Hoc Connection, and **what** was its previous name? _(From page 182)_
- **What** type of accounts does an Ad-Hoc Connection allow you to launch a PSM connection with? _(From page 182)_
- **What** administrative step is noted as a "best practice" when configuring a duplicated Ad-Hoc platform? _(From page 183)_
- **How** do you immediately apply new Ad-Hoc connection policy changes instead of waiting up to 20 minutes for a policy refresh? _(From page 183)_

---

**Topic 4: PSM for Windows & PSM for SSH**

- **What** is PSM for Windows, and **what** was it previously known as? _(From page 186)_
- **How** does connecting via an RDP file bypass the PVWA while keeping CyberArk security intact? _(From page 186)_
- **Why** can a user not connect to a target system using its IP address or a short domain name if the target details must match CyberArk PAM exactly? _(From page 188)_
- **How** do you edit an RDP file's "alternate shell" and "username" lines in Notepad++ to include target system details in advance? _(From page 190)_
- **What** three essential details must be input when manually setting up an external RDP client application to connect via the PSM? _(From page 191)_
- **What** is PSM for SSH, and **what** names was it previously known by? _(From page 191)_
- **How** does a user connect to a target machine through PSM for SSH using a command-line tool like PowerShell (what does the connection string look like)? _(From page 191)_


## 1. EPV & Access Workflows

- What does the acronym EPV stand for, and why is it important to know when modifying privileged access workflows? _(From page 171)_
- What is the Allow EPV transparent connections workflow, and how does the lab guide instruct you to treat this specific setting when deactivating other workflow exceptions? _(From page 171)_

## 2. Platform Exceptions

- What is an exception in CyberArk platform management, and what is its primary purpose if the PSM has been disabled globally through the Master Policy? _(From page 173)_
- How do you structurally add an exception to a platform profile using the PVWA interface, and how do you use the _Session management_ tab to make it work? _(From page 173, 174)_

## 3. The HTML5 Gateway & Parameters

- What is the PSM HTML5 Gateway, and how does it fundamentally change where and how the RDP session window is delivered to the end user? _(From page 176)_
- What are all of the specific hierarchical configuration parameters listed on line `2.` of page 177 that you must navigate through under _Options_ to locate the target `PSM Gateway` node? _(From page 177)_
- What are all of the specific parameter folders and sub-nodes listed on line `1.` of page 179 that you must browse through to locate the `AllowMappingLocalDrives` user parameter? _(From page 179)_
- How does the process of dragging and dropping a file work when moving it in reverse—from the remote machine ACME-123 back to your native workspace machine COMP01? Explain what happens when you drop the file into the mapped directory _Z_. _(From page 182)_

## 4. Remote Connections Client Utilities

- What is mstsc, and how does PSM for Windows utilize standard desktop tools like it or an RDP connection manager to securely handle target system details? _(From page 186)_