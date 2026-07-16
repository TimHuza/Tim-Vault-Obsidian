#journal 


### 1. **CyberArk LAB**
I started a day with a CyberArk lab with Batya. And we completed a [[User Managements 41-58]] section there. I reviewed the [[Introduction To CyberArk PAM 13-40]] and what we did today [[User Managements 41-58]].

I also learned some variables in `dbparm.ini` [[dbparm.ini File Explained|file]] 


### 2. **VS-Code Documentation**
Today I completed the [[Agents Window]] section and was just reading a documentation.

### **2.1. VS-Code Documentation Update**
Today I also read about [[July 15, 2026 VS Code Update]]. Some new things:
The Visual Studio Code 1.129 update includes several major updates, primarily focused on AI integration and interface refinements. Here are the key features with concise descriptions:

- **The Agent Host**: A dedicated process for AI sessions (Copilot, Claude, Codex) that allows one session to be used across multiple windows.

- **Experimental Editor Panel**: A redesigned Agents window pane that merges chat and file diffs into a single, docked area with shared tabs.

- **Terminal Commands in Chat**: You can now run commands directly from chat prompts by using the **`!` prefix**.

- **Modern UI Preview**: An experimental setting to test a modernized look for the VS Code workbench.

- **Agent Session Management**: AI agents can now list, create, and send messages to other chat sessions to handle sub-tasks.

- **Improved New-Session Flow**: The session picker now remembers your previous settings and uses a simple checkbox for Git worktree isolation.

- **GitHub Enterprise Support**: Copilot on the agent host now supports authentication through GitHub Enterprise (GHE) instances.

- **BYOK Model Support**: Use "Bring Your Own Key" models with the Copilot harness in the Agents window.

- **Prompt Migration Tool**: An experimental tool to convert local `.prompt.md` files into "skills" for better compatibility across agents.

- **"Reopen Editor With" Menu**: A new toolbar menu that makes it easier to switch between different editor types for the same file.

- **Custom Editor Priorities**: New APIs that allow custom editors to opt out of being the default for diff or merge views.


### **3. Cyber Security**
I reviewed previous course materials and discovered that 3 lessons were add in **Section 7: AI & Cyber Security** sections. I was doing one lesson in that section


### **4. Django**
Today I started another course Heavy Aura with s6ptember because the ENF one is a bit difficult. Today I did a lot of work and you can see all the things I did in my [github repository](https://github.com/TimHuza/Heavy-Aura-Django-Shop).

Today I also learned about
- [[linebreaks Explained]]
- Media 
	- [[Media in urls.py Explained]]
	- [[Media in setting.py Explained]]
- [[models.py File Explained]]

> In Django templates, `|linebreaks` is a **template filter** that converts line breaks (`Enter` keys) in text into HTML paragraphs and line breaks.
> It is basically like in python `\n`
> 
> `|linebreaks` = `\n`


```Python
if settings.DEBUG:
    urlpatterns += static(
        settings.MEDIA_URL,
        document_root=settings.MEDIA_ROOT
    )
```
The purpose of this code is:

> **Tell Django how to serve uploaded files (images, videos, documents) during development.**


```Python
MEDIA_URL = '/media/'

MEDIA_ROOT = BASE_DIR / 'media'
```

#### 1. `MEDIA_ROOT`

```python
MEDIA_ROOT = BASE_DIR / 'media'
```

##### Meaning:

`MEDIA_ROOT` tells Django:

> "Save uploaded files inside this folder."

#### 2. `MEDIA_URL`

```python
MEDIA_URL = '/media/'
```

This tells Django:

> "When someone requests a media file, use this URL prefix."



### **5. Python AI Agents**
Today I improved on my functions:
- `summarize_agent`
- `organize_agent`
- `permission_agent`

More changes are in my [File-Organizer-Agent](https://github.com/TimHuza/File-Organizer-Agent) repository
