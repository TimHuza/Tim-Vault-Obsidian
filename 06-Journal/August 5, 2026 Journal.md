#journal 


### **1. Django Teacher Agent**
Today I was making my own Django teacher agent that I will to use to learn Django. He can
- Explain concepts
- Write code
- Test and debug the code
[[0.1v. Planning The Project]]

I discussed what is [[Thinking Effort]] and [[AI model pricing or usage units]]

I also bought and [[GitHub Copilot Pro]] $10 subscription.

Here is the [repository](https://github.com/TimHuza/django-teacher-agent) of it.

### 1.2 VS Code August 5 Update
Today I read the [[August 5, 2026 VS Code Update]]

The August 5, 2026, release of **Visual Studio Code (version 1.132)** introduces several major enhancements focused on AI agent collaboration, voice interaction, and editor flexibility.

#### **AI Agent & Chat Improvements**

- **Agent Host & Multi-Window Support**: A new agent host process allows you to connect to the **same agent session from multiple VS Code windows**. This host supports harnesses like Copilot, Claude, and Codex.
- **Agents Window**: A dedicated space now exists to monitor multiple sessions. It features **live status pills** to track changes, view Markdown previews, follow subagents in separate chats, and monitor agent interactions within the integrated browser.
- **Side Chats (/btw)**: You can now ask contextual questions using the **`/btw` command** in the chat input. This allows you to query the current agent turn or response without interrupting the primary conversation flow.

#### **Enhanced Voice & Dictation**

- **Multilingual Dictation**: Dictation now uses the **Nemotron 3.5 on-device model**, which supports automatic language detection or follows your specific language settings.
- **Shell-Aware Terminal Dictation**: When dictating commands in the terminal, the system now applies **shell-aware cleanup**. For instance, saying "git commit dash m hello world" will correctly format as `git commit -m "Hello World"`.
- **Onboarding Experience**: A new voice onboarding flow includes a live microphone waveform and device picker to help users verify their setup.

#### **Editor & Browser Enhancements**

- **Commenting in the Integrated Browser**: Using `Ctrl+Alt+C`, you can now **comment on specific web page elements** within the integrated browser to provide precise feedback to AI agents.
- **Markdown Diffs**: The experimental hybrid Markdown editor now supports **live diffs**, allowing you to review rendered changes with gutter indicators while continuing to edit the document.
- **Editor Type Switching**: The Agents window and breadcrumb bar now include a dropdown to quickly **switch between regular and diff editors** without needing separate commands.

#### **Terminal & Administrative Changes**

- **Terminal Output Reflow**: Terminal output within the Chat view now **reflows dynamically** when the view is resized, preventing early line wrapping.
- **Agent Host Policy**: The `ChatAgentHostEnabled` policy has been removed, meaning administrators can no longer centrally disable the agent host, though individual developers can still toggle it via settings.

I noticed an infographic regarding these source materials is currently being generated for you. It should be available in your artifacts shortly.

The Infographic of the update:
![[agust-5-update.png|700]]


### **2. Cyber Security**
Today I did the 3. NAT, Private & Public IP Addresses lesson in Network Essentials section.
#### **1. NAT (Network Address Translation)**

**NAT** is a service that allows multiple devices on the same home network to share just **one single public IP address**.

- **Public IP Address:** This is the one "official" address given to your router by your Internet Service Provider (ISP).
- **Private IP Address:** These are "internal" addresses assigned to each of your devices by your router. For example, your laptop might be `192.168.1.10` and your phone `192.168.1.11`.

|Feature|Private IP Address|Public IP Address|
|:--|:--|:--|
|**Who uses it?**|Your internal devices (Phone, TV, Laptop).|Your Router (to talk to the internet).|
|**Is it unique?**|Only unique inside your own house.|Unique across the entire internet.|
|**Who gives it to you?**|Your Router.|Your Internet Service Provider (ISP).|

I also did the quiz on 8/10 for this
![[3-nat-quiz.png|411]]


### **3. AI Project**
Today I was fixing code so it can be ready for testing I also created an issue that I will close when I will solve the issue.

[Repository](https://github.com/TimHuza/File-Organizer-Agent)