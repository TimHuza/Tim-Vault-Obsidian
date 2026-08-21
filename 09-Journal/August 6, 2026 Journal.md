#journal 


### **1. [[Smart File Organizer Agent]]**
Today I was closed my two issues that I created yesterday and was trying to run and test the agent. Overall, the agent is not yet ready. There is a [repo](https://github.com/TimHuza/File-Organizer-Agent) to this agent


### **2. Cyber Security**
Today I did a 10. The DNS System video in Network Essentials section for course.

#### **What is DNS?**

DNS stands for **Domain Name System**. It is responsible for translating human-friendly names (like `google.com`) into the numerical **IP addresses** (like `192.168.1.1`) that computers actually use to talk to each other.

*   **The Analogy:** DNS is the **phone book of the internet**. Instead of memorizing every person’s phone number, you just look up their name.

#### **The DNS "Chain of Command" (Hierarchy)**

When you look up a website, your request goes through a specific order of servers:

1.  **Root Name Servers:** The top level that starts the search.

2.  **Top-Level Domain (TLD) Servers:** These manage extensions like `.com`, `.org`, or `.edu`.

3.  **Authoritative Name Servers:** These hold the "final answer" and the actual IP address for the website.

#### **The Resolution Process**

When you type a website into your browser:

*   Your computer asks your **ISP (Internet Service Provider)** for the address.

*   If the ISP doesn't have it saved (in its cache), it asks the **Root Server**.

*   The Root Server sends it to the **TLD Server** (like the `.com` server).

*   The TLD Server sends it to the **Authoritative Server**, which provides the final IP address.

*   Your browser finally connects to the website.

I also did a quiz on 7/10.
![[the-dns-system-quiz.png]]


### **3 Django**
Today I was doing code following the course instructor

### 4. Django Teacher Agent**
Today I made a runbook feature to my django teacher agent and a [v1.1.0 Runbook Release](https://github.com/TimHuza/django-teacher-agent)

This release adds runbook saving support to the Django Teacher Agent. The agent now records final user-facing responses as Markdown runbook files before sending them in chat, which improves traceability, reviewability, and project documentation.

I have an idea for a new feature:
🚀 Django Teacher Agent will automatically push your runbook responses directly into your Obsidian vault. No more manual copy-pasting — your explanations, debugging notes, and learning records are saved instantly.