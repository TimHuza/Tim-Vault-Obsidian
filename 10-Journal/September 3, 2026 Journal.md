#journal 


### **1. AI Agent Builders Community**
Today I was really active in this community. I completed **Module 1**
- [[12 Terms You Need Now - Module 1]]
- [[Reference Glossary - Module 1]]
- [[The Five Layers of an AI Agent - Module 1]]

And started **Module 2**

I also posted a [[My First AI Project - Post|post]] about my first AI project and honestly I got amazing feedback.

---

### **2. Cyber Security**
Today I did lessons **58. Introduction to Proxy Servers** and **59. Introduction to Virtual Private Network (VPN)** in Section 9: Privacy, Anonymity & VPNs

#### 58. Introduction to Proxy Servers

#### 1. What is a Proxy Server?

A **proxy server** is a digital middleman (an intermediary) that sits right between your computer and the website you are trying to visit.

- **The Analogy:** Imagine you want to ask a question to someone you don't know, but you don't want them to know who you are. Instead of walking up to them yourself, you write your question on a piece of paper and hand it to a friend (the proxy). Your friend walks over, asks the question, gets the answer, and brings it back to you. The stranger only ever saw and talked to your friend, not you.
- **The Technical View:** Instead of your computer connecting directly to a website's server, your web request goes to the proxy first. The proxy then forwards your request to the website on your behalf.

#### 2. How a Proxy Helps You (The Advantages)

Using a proxy server provides several key benefits for basic privacy and web browsing:

- 🕵️ **Hides Your Real IP Address:** Because the proxy makes the request for you, the destination website only sees the **proxy's IP address** instead of your home IP address.
- 🌐 **Bypasses Restrictions and Censorship:** If your school, workplace, or country has blocked a website, you can use a proxy server located in a different region to access it.
- 🔒 **Obscures Destination from Your ISP:** A proxy makes it much harder for your Internet Service Provider (ISP) to see the exact, specific webpage you are visiting.
- 📥 **Safer Torrenting:** Proxies can be configured to hide your personal IP address from other uploaders and downloaders (peers) when using torrent networks.

#### 3. The Big Problems with Traditional Proxies

While proxies are highly useful, they are **not** complete security tools. In cybersecurity, we must always watch out for three major drawbacks:

##### A. Reduced Speed and Performance

Because all your internet traffic has to travel to an extra server before it reaches its destination, using a proxy will often **reduce your internet speed and increase latency**. How much it slows down depends entirely on the quality of the proxy server you are using.

##### B. A Critical Lack of Encryption

This is a vital exam concept! Traditional proxies **do not necessarily encrypt your traffic**.

- While some modern proxies might encrypt the connection between your computer and the proxy itself, they do not guarantee full, end-to-end encryption across the entire internet.
- **The Golden Rule:** A proxy is **not** a replacement for encryption or a Virtual Private Network (VPN). If you send sensitive data (like a password or credit card) over a traditional proxy, it could still be read by someone intercepting the data.

##### C. Trust and Reliability Issues

When you use a proxy, you are trusting the owner of that proxy with your data. Free proxy servers are often incredibly busy, overloaded, or completely offline.

- Before using any proxy, you must perform **due diligence**. This means researching their:
    - **Reputation:** Who owns it, and do they have a history of stealing data?
    - **Reliability & Speed:** Does it stay online and perform well?
    - **Security Practices:** How do they handle your logs and connection?

#### 4. The Login Trap: Why You Aren't Completely Anonymous

A very common beginner mistake is thinking that a proxy makes you completely invisible online.

- A proxy hides your physical location (IP address), but **if you log into an account (like Facebook, Google, or Twitter), the website immediately knows exactly who you are**.
- The moment you type in your username, the website bypasses your IP shield and links all your active browsing session habits directly back to your personal profile.

#### 5. Examples of Web Proxy Services

The lesson highlights three web proxy services that you can use to browse privately:

1. **Hidester:** This service offers proxy servers in both the US and Europe. It includes security features like **URL encryption**, cookie controls, script removal (which blocks malicious code), and the ability to modify your browser and operating system details so sites cannot easily "fingerprint" your device.
2. **Hide.me:** A completely free web proxy with physical servers located in the Netherlands, Germany, and the United States. It allows you to control cookies, remove active scripts, and turn on page encryption.
3. **ProxySite:** Designed to help you bypass restrictions and access major blocked sites like YouTube, Facebook, and Twitter using various server locations.

### Study Guide Quick-Recall Cheatsheet

|Feature|Proxy Server|
|:--|:--|
|**What is it?**|A single middleman sitting between you and the web.|
|**What does it hide?**|Your public IP address (replaces it with the proxy's IP).|
|**Does it encrypt?**|No, traditional proxies generally **do not** provide end-to-end encryption.|
|**Main Advantage**|Excellent for bypassing local web blocks and censorship.|
|**Main Drawback**|Can be slow, unreliable, and requires complete trust in the proxy owner.|
|**The Logging Threat**|If you log into an account, your proxy protection is bypassed.|

**Key Takeaway for your notes:** A proxy server is a single middleman that hides your IP and lets you bypass web blocks. However, it **does not guarantee encryption** and **cannot protect your identity if you log into your personal accounts**.

![[58-lesson-infographic.png]]

I also did a quiz on 8/10
![[58-proxy-lesson-quiz.png]]


#### 59. Introduction to Virtual Private Network (VPN)

#### 1. What is a VPN?

A **Virtual Private Network (VPN)** is a security tool that lets you send and receive data over the internet while protecting your privacy.

Just like a proxy, a VPN sits right between your device and the rest of the internet:

```
You ➔ VPN Server ➔ Internet
```

However, a VPN is far more powerful than a basic proxy because **it encrypts (scrambles) all the traffic traveling between your computer and the VPN server**.

#### 2. How a VPN Works (The "Encrypted Tunnel")

To understand how a VPN keeps you safe, look at the difference in how your data travels:

- **Normal Internet Connection:**
    
    ```
    You ➔ Internet
    ```
    
    Without a VPN, your data travels in the open. Your Internet Service Provider (ISP) or anyone snooping on your network can easily see your IP address, your search requests, and the websites you visit.
    
- **VPN Connection:**
    
    ```
    You ➔ Encrypted Tunnel ➔ VPN Server ➔ Internet
    ```
    
    When you turn on a VPN, it builds a secure, **encrypted tunnel** for your data. The VPN automatically encrypts:
    
    - Your web requests.
    - Your IP address.
    - All the traffic between your computer and the VPN server.
    
    _Note for your notes:_ The connection between the **VPN server and the final website** is not necessarily encrypted by the VPN itself.

#### 3. VPN vs. Proxy: What's the Difference?

This is a very common exam topic! While they look similar on the surface, they handle security very differently:

|Feature|Proxy Server|VPN|
|:--|:--|:--|
|**Acts as a middleman?**|✅ Yes|✅ Yes|
|**Hides your public IP?**|✅ Yes|✅ Yes|
|**Helps bypass local blocks?**|✅ Yes|✅ Yes|
|**Encrypts traffic to the server?**|❌ No (Usually not)|✅ Yes (Always)|
|**Provides complete privacy?**|❌ No|❌ No|

#### 4. Real-World Uses of VPNs

Why do people and companies use VPNs every day? The source highlights three major reasons:

##### 💻 A. Working Remotely (Business Intranet)

In the business world, VPNs are extremely popular. They allow employees to securely log into their company's private internal network (**intranet**) from another city, another country, or anywhere outside the physical office.

```
Employee ➔ VPN ➔ Company Network/Intranet
```

##### 🚫 B. Bypassing Restrictions and Censorship

If your ISP, school, or country blocks access to certain websites, a VPN helps you bypass those censorship walls by routing your connection through a different region.

##### ⚡ C. Beating "ISP Throttling"

Normally, using a VPN can **reduce your internet speed** because your traffic has to travel through an extra server before reaching its destination. However, there is a cool exception where a VPN can actually make your internet feel _faster_:

- **What is ISP Throttling?** Some internet providers deliberately limit your bandwidth or slow down specific types of traffic (like video streaming), even if you have an "unlimited" plan. For example, Verizon has previously throttled plans to limit video quality to 480p on smartphones, or 720p/1080p on tablets.
- **The VPN Fix:** When you use a VPN, your ISP can only see that you are using an encrypted tunnel—they can no longer see _what_ you are doing (like watching a video). Because they can't identify the traffic, they can't throttle it, which can actually **improve your effective speed or video quality**!

#### 5. The Big Limitation: You Are Not Invisible

The most important rule to remember for your studies is that **a VPN provides optimal privacy in theory, but it does not provide total anonymity**.

- A VPN hides your IP address and encrypts your data path.
- However, if you log into your personal accounts (like Google or social media), those websites still know exactly who you are, completely bypassing the VPN's protection.


**Key Takeaway for your notes:** A VPN acts as a secure middleman that hides your IP address and protects your data inside an **encrypted tunnel**. It is widely used by businesses for remote work and by regular users to bypass censorship and **ISP throttling**, but it **cannot** guarantee 100% total anonymity.

![[59-lesson-infographic.png]]

I also did a quiz on 8/10
![[59-vpn-lesson-quiz.png|421]]

---

### **3. VS Code Update**
Yesterday on September 2 a VS Code [[September 2, 2026 VS Code Update|update]] was released.

Moving forward to the **September 2, 2026 (version 1.136) update**, this release centers heavily on managing agent-driven workflows across complex workspaces and organizing related chat sessions.

#### Agent Orchestration & Workflows

- **Agent Merge (Preview)**: To help you take a pull request across the finish line, you can now delegate the resolution of review feedback, failed checks, and merge conflicts directly to an agent. The agent repeats the process and reruns workflows until the PR is ready to merge.
- **Navigate Related Chats and Sessions**: You can now organize related chats into a parent-child session hierarchy in the Agents window. Instead of dealing with a cluttered list of unrelated sessions, you can easily track which chats belong together, see individual statuses and pending approvals, and navigate back to initiating sessions via direct links.
- **Redesigned New-Session Input**: Starting delegated agent work requires less setup with a layout that brings model selection, workspace selection, prompts, and session controls together.

#### Workspace & Editor Enhancements

- **Experimental Multi-Root Workspaces**: Copilot and Claude agent sessions in the editor window Chat view now support multi-root workspaces. If custom agent hooks are detected in multiple folders, VS Code will prompt you to select the primary folder.
- **Project Name Workspace Resolution**: Agents can now resolve workspaces using their project name (e.g., "run this in the vscode workspace") rather than requiring absolute paths.
- **Compact Layout Density (Experimental)**: To fit more content into your editor window, you can enable a "Compact" layout density that removes the spacing between panels and reduces inner panel spacing.

#### Personalization & Settings

- **Chat Backgrounds (Experimental)**: You can personalize the Agents window with built-in theme-aware icon patterns (like Codicons) or your own uploaded images. It features 11 layout options (including stretch, repeat, and center) and automatically swaps backgrounds when you change between dark and light themes.
- **Agent Session Notifications**: You can now get system notifications when an agent session requires input or finishes its work while the VS Code window is unfocused.
- **Enterprise Dictation Controls**: Administrators can now manage dictation data through policies that enforce local, on-device transcription and disable cloud-based language-model cleanup.

#### Additional Quality of Life Improvements

- **Integrated Browser Spell Check**: You can now right-click a misspelled word in any editable field inside the integrated browser to get spelling suggestions or add it to your dictionary.
- **Faster Terminal Startup**: Extension-run terminal commands—such as starting the JavaScript debugger—no longer suffer from a brief delay (up to 5 seconds under certain timing conditions) once shell integration is ready.
- **"The Story of VS Code" Premiere**: VS Code is celebrating its history with a special documentary premiere on September 4, 2026, at 8:00 AM PT.

![[september-2-vscode-update.png]]