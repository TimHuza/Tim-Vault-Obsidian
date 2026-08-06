#journal 



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