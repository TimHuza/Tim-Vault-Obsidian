#journal 


### 1. **CyberArk**
Today I did a lab with batya. [[Securing Windows Domain Accounts 59-72]]
And I studied topics:
- [[What is GPO]]
- [[How GPO + CyberArk works]]
- [[!Dom Cybr 15 Platform Parameters]]
- [[Automatic Password Management (Params)]]
- [[UI & Workflows (Parameters)]]
- [[What is Platforms]]
- [[Why Need Platforms]]
- [[How Reconcile Account works]]
- [[What is Reconcile Account]]
- [[What is Regression Express]]
- [[What is Active Directory]]

> **GPO = Group Policy Object**
	A **GPO is a set of rules/settings that an administrator creates to control Windows computers and users in a company.**
	
#### Platform
> A **Platform** is a set of rules that tells CyberArk how to manage a certain type of account.

#### Parameters
1. [[UI & Workflows (Parameters)|UI & Workflows]]
> **"How should people interact with these accounts?"**

2. General Properties
> This section contains the platform's **general settings**.

#### Reconcile Account
> A **Reconcile Account** is a special privileged account that CyberArk uses to **fix (synchronize) passwords when CyberArk loses control of an account password**.

#### Active Directory (AD)
> **Active Directory (AD)** is a Microsoft system that organizations use to:
	- 👤 Manage users
	- 💻 Manage computers
	- 🔐 Control access
	- 📜 Apply security rules
	- 🏢 Organize company resources


### 2. **VS-Code Documentation**
Today on VS Code documentation I practiced the [[Chat View]]. By asking the chat:
- `What was my last commit message?`
- `Create an app ....`
All changes are in my [GitHub repo](https://github.com/TimHuza/VS-Code-Documentation)

Then I finished the [[Remote Agent Sessions]] section and learned [[What is Session or Sessions]]


### **3. CyberSecurity**
I finished `44. Demo - How Generative AI Makes Phishing More Convincing` lesson.


### **4. Django**
Today on Django I was coding and resolving the problems.
- CSS not working
- Categories are not showing app on the left side bar

Also I learned what is [[Paginator Import Explained|Paginator]] in import and discussed with ChatGPT the [[urls.py slug Explained]]

> Paginator **splits a large list into smaller pages.** 

Suppose your products are
```
1 Apple
2 Banana
3 Orange
4 Pear
5 Kiwi
6 Mango
7 Peach
8 Lemon
9 Cherry
10 Plum
11 Grape
12 Melon
13 Coconut
14 Lime
15 Pineapple
```

Now create

```python
Paginator(products, 5)
```

Django divides them into:

```
Page 1
------
Apple
Banana
Orange
Pear
Kiwi
```

```
Page 2
------
Mango
Peach
Lemon
Cherry
Plum
```

```
Page 3
------
Grape
Melon
Coconut
Lime
Pineapple
```


### **5. Git & GitHub**
Today I reviewed [[What is Pull Request (PR)|Pull Request]] topic and learned about [[How to Work in 2 branches]]