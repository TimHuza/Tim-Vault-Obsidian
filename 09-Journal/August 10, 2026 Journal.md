 #journal 


### **1. Django Teacher Agent**
Today I was trying to do the MCP connection so my runbooks would save to obsidian

### **2. Cyber Security**
Today I finished the **11. How Data Travels the Internet** and **12. Common Networking Tools & Commands** lessons in network essentials section number 3

#### **11. How Data Travels the Internet**
#### Step 1: Your Home Network (LAN)

Your device (laptop, phone, or tablet) is called an **endpoint**. When you type a website address:

*   The request goes to your **router**.

*   **NAT (Network Address Translation):** The router changes your device's "Private IP" into a "Public IP" so the internet knows where the request came from.

*   **Security:** Even at this stage, things like your device's **firewall** and **HTTPS** encryption start protecting your data.

#### Step 2: The ISP (Your Internet Provider)

The request travels from your router to your **Internet Service Provider (ISP)**.

*   The ISP acts like a local post office. It looks at your request and tries to find the website's digital address using **DNS**.

#### Step 3: Finding the Address (DNS Resolution)

If the ISP doesn’t know the address yet, it uses the **Domain Name System (DNS)** to find the exact server where the website "lives".

*   **Security Tip:** A tool called **DNSSEC** can be used here to prevent "DNS spoofing," which is when a hacker tries to send you to a fake website instead of the real one.

#### Step 4: The Web Server (The Destination)

The request finally reaches the **Web Server** hosting the site.

*   The server checks that your request is safe using its own **firewalls** and **SSL/TLS certificates** (this is what makes the "lock" icon appear in your browser).

#### Step 5: The Return Trip

The data travels all the way back: **Web Server → ISP → Your Router → Your Device**.

*   The router uses **NAT** one last time to make sure the data goes to your specific phone or laptop, and not someone else's device in your house.

I also did quiz on 7/10 on this lesson
![[quiz-11-data-travels-the-internet.png]]

#### **12. Common Networking Tools & Commands**
#### 1. Ping (Checking "Are you there?")

The **ping** command is the simplest way to test if a website or device is reachable.

*   **Why it's useful:** It is very fast and great for a quick "basic connectivity" check.

#### 2. Tracert / Traceroute (The "Road Map")

While ping just tells you if a site is "up," **tracert** (Windows) or **traceroute** (Linux/Mac) shows you the exact path your data takes to get there.

#### 3. Nslookup (The "Phone Book Search")

**nslookup** is used to find information from the Domain Name System (DNS).

*   **Forward Lookup:** You give it a name (google.com) and it gives you the IP address (142.250.x.x).

*   **Reverse Lookup:** You give it an IP address to see what domain name is associated with it.

*   **Note:** This can be tricky because **multiple websites** often share the same single IP address if they are on a "shared host".

#### 4. Reverse IP Lookup & Whois (The "Background Check")

*   **Reverse IP Lookup:** This tool helps you find *every* domain name that is sharing a specific IP address.

*** 

**Key Takeaway for your notes:**

*   **Ping** = Check if it's alive.
*   **Tracert** = See the path it takes.
*   **Nslookup** = Find the IP or Name.
*   **Whois** = Find out who owns it.

I also did a quiz on 8/10
![[quiz-12-common-networking-tools-commands.png]]