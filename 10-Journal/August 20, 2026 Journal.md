#journal 


### **1. VS Code**
Today I did a VS Code section for the Saturday presentation. There is a [repository](https://github.com/TimHuza/aug-22-sat-pres) for this Saturday day 22 August.


### **2. VS Code Update**
There is also a new VS Code update that I read about:

Following up on the August 5 release, the subsequent **August 19, 2026 (version 1.134) [[August 19, 2026 VS Code Update|update]] focuses on helping you work across windows, organizing related chats side-by-side, and navigating long conversations more efficiently.

#### Side-by-Side Chat Layouts & Navigation

- **Grid Layout for Chats**: You can now arrange related conversations and subagent chats into horizontal or vertical groups to compare results or monitor work side by side. You can drag and drop chats into groups, or Alt+select a chat in the Chats picker to open it to the side. VS Code automatically restores this layout and focus when you return to the session or reload the window.

- **Prompt Timeline**: To make navigating long agent sessions easier, the Agents window now includes a timeline in the transcript gutter where each dot represents a prompt. Hovering displays the prompt, selecting it jumps to it, and for prompts that changed files, it shows the number of lines added and removed and lets you open the changes directly. You can also configure this timeline to show beside the scrollbar (ruler) or hide it completely.

- **Find in Chat**: You can now use `Ctrl+F` to search through the entire chat history in the Chat view, chat editors, and the Agents window. This search covers the complete conversation—including off-screen, unrendered content—and automatically scrolls matches into view while expanding collapsed work summaries where matches occur. It also supports case matching, whole words, and regular expressions.

#### Agent Host and Layout Enhancements

- **Agent Host Capabilities**: The agent host lets you connect to the same agent session from multiple VS Code windows. It runs agent harnesses in a dedicated process based on the Agent Host Protocol (AHP), aligning the Copilot agent's behavior and functionality with the Copilot CLI, standalone app, and other Copilot products via the Copilot SDK.

- **Side Pane Improvements**: Under the single-pane layout (`sessions.layout.singlePaneDetailPanel`), session details and editors share a tab bar next to chat. This layout now respects your tab visibility settings, features file breadcrumbs in the headers for text file editors, and maintains its size and visibility when you switch sessions to prevent unexpected layout shifts.

#### Editor & Browser Controls

- **Previewing HTML by Default**: If you regularly preview local HTML files instead of editing them, you can set the integrated browser as their default editor via the `workbench.editorAssociations` setting or directly from the editor header. The integrated browser maintains its association with the HTML file by opening links and navigation in new tabs.

- **Close Other Editors Shortcut**: You can now keep a single editor open without using the tab context menu by holding `Alt`, which changes the close action on each editor tab to **"Close Other Editors"**

🎨 Now that you have the overview of the latest August 19 update, let me know if you want to dive deeper into how the new Agent Host works, or if you'd like to look at the community contributions from this release.

![[august-19-vscode-update.png|700]]


### **2. Cyber Security**
Today I did 50. Access Control Models lesson in Identity & Access Management section.

![[access-control-models-infographic.png]]
#### 1. DAC (Discretionary Access Control) — "The Owner Decides"

- **What it is:** In this model, the **resource owner** (the person who created the file or folder) gets to decide who is allowed to look at it or change it.

- **The Building Analogy:** You have your own private office. You hold the key, and you can choose to let your friend in, give a copy of the key to a coworker, or keep the door locked.

- **Best Use:** Best for small teams and personal computers where setting up complicated rules is not necessary.

- **Pros:** Very easy to set up, highly flexible, and simple to manage.
- **Cons:** High risk of **oversharing**. Because individual users control access, a coworker might accidentally share a secret file with the wrong person.

---

#### 2. MAC (Mandatory Access Control) — "The System Authority Decides"

- **What it is:** Access is strictly controlled by a **central authority** (like an IT department or security team) using preset security labels. Individual users have no say in who gets access—even if they created the file.

- **The Building Analogy:** A military base. Every room and document has a clearance stamp (like "Confidential" or "Top Secret"), and every person has a badge with their clearance level. If your badge says "Secret," you cannot open a door marked "Top Secret," no matter who you ask.

- **Best Use:** Used almost exclusively in **military and government systems** where security is the absolute highest priority.

- **Pros:** Extremely secure and very difficult for hackers to bypass.
- **Cons:** Inflexible and hard to change quickly when employee roles or business needs shift.

---

#### 3. RBAC (Role-Based Access Control) — "The Job Decides"

- **What it is:** Instead of giving permissions to individual people, permissions are assigned to **job roles**. When an employee is hired, they are placed into a role, and they automatically get the access associated with that job.

- **The Building Analogy:** In a hospital, anyone wearing a "Doctor" badge can enter the patient rooms. Anyone wearing a "Billing Clerk" badge can enter the accounting office. You get access based on your uniform, not your name.

- **The Big Risk — Role Creep:** This is a major test topic! **Role creep** happens when an employee changes departments (for example, moving from Finance to HR) but the company forgets to remove their old permissions. They end up with access to both Finance and HR systems, which violates the Principle of Least Privilege.

- **Best Use:** Large organizations and businesses where managing permissions one person at a time would be impossible.

- **Pros:** Highly scalable and incredibly easy for IT departments to manage as people join or leave the company.

---

#### 4. ABAC (Attribute-Based Access Control) — "The Conditions Decide"

- **What it is:** This is the most precise and advanced model. It makes access decisions by looking at specific **attributes** (characteristics) of the user, the resource, and the environment.

- **Common Attributes Evaluated:**
    - **User attributes:** Their department, identity, or clearance level.
    - **Resource attributes:** How sensitive the file is.
    - **Environment attributes:** The time of day, the user's location, the device they are using, or their IP address.

- **The Building Analogy:** You can only enter the server room if: you are an IT Administrator (user attribute) AND it is between 9:00 AM and 5:00 PM (environment attribute) AND you are swiping in from a company-approved badge reader inside the physical building (environment attribute).

- **Best Use:** Complex, modern business environments that need very detailed and specific security rules.

- **Pros:** Extremely flexible and highly precise.
- **Cons:** Highly complex to configure and difficult for IT teams to maintain over time.

#### Study Guide Quick-Recall Cheatsheet

| Model    | Memory Trick          | Who Decides?                     | Biggest Drawback                         |
| :------- | :-------------------- | :------------------------------- | :--------------------------------------- |
| **DAC**  | **Owner** decides     | The person who owns the resource | Risk of oversharing                      |
| **MAC**  | **Authority** decides | Central system security rules    | Highly inflexible                        |
| **RBAC** | **Role** decides      | The user's job title             | **Role creep** (keeping old permissions) |
| **ABAC** | **Attributes** decide | Multiple specific conditions     | Highly complex to set up                 |

I also did quiz on 8/10
![[access-control-models-quiz.png]]

