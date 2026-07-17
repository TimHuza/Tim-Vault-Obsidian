#journal 

### 1. **VS-Code Documentation**
Today on VS Code documentation I finished:
- [[Agents Window]]
- [[Chat View]]

> The Chat view is where you work with agents in Visual Studio Code while staying focused on the code in your current project.
> ![Screenshot showing an agent session in the Chat view alongside the editor in VS Code.](https://code.visualstudio.com/assets/docs/agents/agents-overview/chat-sessions-view.png)



### **2. Cyber Ark**
Today on Cyber Ark I've studied this image again
![[lifecycle-of-a-cyber-attacks.png|503]]

1. **Initial Penetration:** The attacker attempts to gain access to the company, either from the outside or from within if they already have limited access.

2. **Bypassing Defenses:** The attacker overcomes the organization's security measures, such as the external network perimeter.

3. **Privilege Escalation:** Starting with standard access, the attacker works to gain higher-level permissions, aiming to become an administrator.

4. **Lateral Movement:** Once higher rights are obtained, the attacker moves through the network, accessing different computers.

5. **Information Discovery:** The attacker searches the network for sensitive and important information.

6. **Iterative Progression:** The attacker repeats these steps, as each successful action opens new opportunities to get closer to their ultimate target.

7. **Final Execution:** The attacker achieves their goal by either stealing data or completely disrupting business operations.


### **3. Django**
Today on Django I coding work. I made
- `list.html` - template
- `urls.py` - in `/main` app folder
- reviewed the [[Media in setting.py Explained]] and [[Media in urls.py Explained]]


### **4. Git & GitHub**
Today I discussed with ChatGPT
- [[What is Merge]]
- [[What is Pull Request (PR)]]

#### Merge

> A **merge** is the process of **combining the history of two branches into one**.

You create a new feature branch.

```
main

A --- B --- C
             \
feature       D --- E
```

Now you have two separate histories.
- `main` still ends at **C**
- `feature` has two extra commits **D** and **E**

Eventually your feature is finished. Now you want those commits on `main`.
That's what **merge** does.

#### Pull Request (PR)

> A **Pull Request (PR)** is a request to merge one branch into another.

Think of it as saying:
> "I've finished my work. Could someone review it before we merge it into the project?"

It does **not** merge automatically. Someone (or you) must approve it.