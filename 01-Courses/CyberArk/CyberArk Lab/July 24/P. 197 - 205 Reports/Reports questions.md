#cyberark-labs 

**Topic 1: PVWA Modern Interface Reports**

- **What** is CyberArk’s rule regarding strict compartmentalization of information, and how does it limit which reports a user can generate? _(From page 197)_
- **What** are the three specific groups that reports are divided into when clicking _Generate Report_? _(From page 197)_
- **Why** is the user _Cindy_ specifically chosen to generate reports in this lab exercise? _(From page 197)_
- **What** categories or options are available to filter a _Privileged Accounts Inventory_ report before generation? _(From page 198)_
- **How** do you generate a report without having to wait for a scheduled output, and **what** setting option do you click? _(From page 198)_
- **How** do you download the completed report data from the PVWA, and **what** format is the downloaded file? _(From page 199)_
- **What** tool is used to open the downloaded file, and **what** specific format option must you click if asked when saving it to the desktop? _(From page 199)_

---

**Topic 2: Export Vault Data (EVD) Utility**

- **What** is the **EVD** utility, and **what** is its precise function when generating reports with third-party tools? _(From page 200)_
- **What** types of files does the EVD utility export data into? _(From page 200)_
- **How** do you enable the built-in _Auditor_ user inside the PVWA navigation sidebar instead of using the PrivateArk Client? _(From pages 200-201)_
- **How** do you modify the _Auditor_ user’s authentication settings to assign a password? _(From page 201)_

---

**Topic 3: Credential Files & Hardening**

- **What** type of terminal window environment must be used to run the credential file creation commands? _(From page 202)_
- **Why** is it essential to secure the credential file properly, and **what** do the `CreateCredFile.exe` parameters allow an administrator to do to harden it? _(From page 202)_
- **How** do you use Windows File Explorer and Notepad to configure the `Vault.ini` file parameter, and **what** IP address is assigned to it? _(From page 202)_
- **What** is the exact terminal string command written to run `CreateCredFile.exe` to generate the `auditor.cred` file with specified application types and restrictions? _(From page 203)_
- **What** alternative interactive method can you invoke using just the executable parameters plus the output filename to set up file security? _(From page 203)_
- **Why** does the option _"Disable wait for DR synchronization before allowing password change"_ provoke a warning error in the Vault log during this exercise, and **how** should you handle it? _(From page 203)_

---

**Topic 4: Running Data Exports**

- **How** do you execute the main `./ExportVaultData` string command in the terminal to output an activity report? _(From page 204)_
- **What** are the four specific backslash parameters (`\`) inside the execution string used to call the initialization files, set targets, specify logging windows, and define output file targets? _(From page 204)_
- **What** is the name of the generated activities log report file, and **how** many preceding days of vault data does it collect? _(From page 204)_


- What is Reports? How they work? Why we need them?
- What are these three groups of reports:
   • Operational reports • Audit/Compliance reports • List reports
- What is Vault.ini file? How it works? Why we need this file?
- What are the parameters in `Vault.ini` file and why we need them?
 ![[vault-ini-file-params.png]]