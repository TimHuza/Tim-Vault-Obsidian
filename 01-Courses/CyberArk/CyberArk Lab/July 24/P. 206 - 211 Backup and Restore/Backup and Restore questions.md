#cyberark-labs 


**Topic 1: Built-in Users & Lab Setup**

- **What** utility is pre-installed on the server _comp01_ to let you test the backup and restoration of Vault data? _(From page 206)_
- **What** specific administrative account must be used to configure and run this replication utility? _(From page 206)_
- **What** unique administrative rights do the built-in users **Backup** and **Operator** possess under the System branch? _(From page 206)_
- **How** do you activate the _Backup_ and _Operator_ users if they are disabled by default in the training environment? _(From page 206)_
- **What** specific Safe name and account parameters are created to safely run a replication and deletion test? _(From page 206)_

---

**Topic 2: Configuring the Replicator Utility**

- **How** do you navigate via Windows File Explorer to find the Replicator utility folders on server _comp01a_? _(From page 207)_
- **What** parameters and target IP address values must be typed into the `Vault.ini` text configuration file? _(From page 207)_
- **What** specific initialization file must be opened in the same directory to locate the designated output folder of your backup files? _(From page 207)_
- **How** do you access the correct folder path via a standard PowerShell window without needing elevated administrator rights? _(From page 207)_

---

**Topic 3: Hardened Credential Files & Running Backups**

- **What** extra security boundaries (such as specific executable paths and machine protection flags) are written to harden `CreateCredFile.exe` for replication scripts? _(From page 208)_
- **What** is the exact command string written in the prompt to create the hardened `backup.cred` file? _(From page 208)_
- **How** do you execute the primary backup terminal string command using the `./PAReplicate.exe` tool? _(From page 208)_
- **What** visual confirmation message appears at the bottom of the script window if replication completes successfully? _(From page 208)_

---

**Topic 4: Safe Deletion & Restoration Process**

- **How** do you navigate the modern PVWA layout menus to locate and select the `TEST_DELETE` Safe for removal? _(From page 208)_
- **Why** does the system give you a pop-up statement saying a Safe cannot be permanently deleted, and **what** has actually happened to its operational status? _(From page 209)_
- **How** do you use the account search feature to verify that your test assets have truly disappeared from active use? _(From page 209)_
- **How** do you run the recovery command-line string utilizing `./PARestore.exe` to bring back your safe properties? _(From page 210)_
- **Why** can the restoration script **NOT** overwrite the original Safe name during this process, and **how** do you address this constraint using target switches? _(From page 210, 211)_
- **How** do you confirm that your restored account asset (`root10b`) was successfully restored to active visibility? _(From page 211)_


- What is Replicator utility? How? Purpose?
- What is tsparm.ini? How? Purpose?
- What is DPAPI machine protection? How? Purpose?