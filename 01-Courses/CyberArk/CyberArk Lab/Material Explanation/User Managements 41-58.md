#cyberark-labs 


In this section of your lab, you are learning how to **manage the people** who use the digital fortress (CyberArk). Just like a school has principals, teachers, and students, a company has different people who need different levels of access to keep things running safely.

Here is everything you are doing in this section, explained simply:

### 1. Meeting the Team (Know the Players)

Before you start clicking buttons, you look at a list of characters in this story. Everyone has a specific job:

- **Administrator:** The "Super User" who can do everything.
- **Mike (The Boss):** He is the main Vault Admin. He sets the rules for how things work.
- **Cindy (The Guard):** She is an Auditor. Her job is to check the recordings and make sure everyone is following the rules.
- **Dexter (The Helper):** He works at the Help Desk. He helps people when they get locked out.
- **Paul, Tom, and Robert (Team Leaders):** They are Safe Managers for different teams like Linux, Windows, and Oracle.

### 2. Connecting to the Company "Phonebook" (LDAP)

Instead of creating a new account for every single employee inside CyberArk, you connect CyberArk to the company's existing "phonebook" (called **LDAP** or **Active Directory**).

- **Directory Mapping:** This is like a rule book that says, "If someone is in the 'Auditors' group in the company phonebook, give them the 'Auditor' job inside CyberArk automatically".
- **Transparent Users:** These are people who exist in the company phonebook. When they log in, CyberArk recognizes them and lets them in without you having to manually type their names into the system first.

### 3. Creating a Special Rule for the Help Desk

You practice making a **Custom Directory Mapping** for the **Help Desk** team (Dexter’s team).

- **The Mission:** The Help Desk needs enough power to help people but shouldn't be allowed to see the company's biggest secrets.
- **Setting Permissions:** You go into the settings and check boxes to allow them to do three specific things: **Activate users**, **Audit users**, and **Reset passwords**. You leave the other boxes unchecked so they don't have too much power.

### 4. Changing How People Log In

You learn that there are different ways to "knock on the door" of the Vault:

- **PrivateArk Client:** You use this "heavy-duty" tool to change how a user proves who they are (their **Authentication Method**).
- In one exercise, you change the settings so that a user named **Dexter** has to log in using the company phonebook (LDAP) instead of a regular password.

### 5. Rescuing a Locked-Out User (Unsuspending)

Sometimes, people are clumsy! You practice what happens when someone types their password wrong too many times and gets **Suspended** (locked out).

- **The Test:** You intentionally fail a login to lock an account.
- **The Rescue:** You log in as an administrator and go to a special area called **Trusted Net Areas**. You find the "Active" status for the user and click a button to **Activate** them again so they can get back to work.

### Key Terms to Remember:

- **LDAP/Active Directory:** The big list of all employees at a company.
- **Mapping:** Connecting a group of people in that list to a specific job in CyberArk.
- **Suspended:** When a user is temporarily banned from logging in because they messed up their password too many times.
- **EPVUser:** A standard type of user inside CyberArk.

By the end of this section, you've learned how to give people the right amount of power, how to connect to the company's list of employees, and how to help people when they get stuck!