#journal

### 1. VS-Code Documentation
Today on VS-Code Documentation I did a lot of topics like:
- [[User Interface]]
- [[Code Navigation]]
- [[Basic Editing]]
- A little bit of [[Settings]]

Also created one `python` file and `js` file for practice.


### 2. CyberArk
On CyberArk I reviewed the image and [[09 Image Explanation (Technologies Change. Attack Paths Don't.)|discussed]] it with ChatGPT
![[july-10-cyberark.png|483]]

Also learned what is [[Lateral & Vertical Movements|Lateral & Vertical Movement]] attacks
- **Vertical movement** = going UP to get more power (higher privileges)
- **Lateral movement** = moving SIDEWAYS to reach more systems


### 3. Cyber Security
On Cyber Security I've tried to make a quiz on NotebookLLM and I've completed **38. Authentication Quiz** and I got 7/10 right. Here are the results:
![[july-10-cyber-security-quiz-results.png|319]]

I also completed **44. BYOD** lesson.

> 💻BYOD (Bring Your Own Device)
> 	it is a policy where employees use their **personal** smartphones, laptops, or tablets for work-related tasks, like checking company emails or working from home

#### Why Use It? (The Good)
- **Productivity:** You can work from almost anywhere
- **Flexibility:** You get to use the devices you are already familiar with and comfortable using.
#### Why is it Risky? (The Bad)
- **Lack of Control:** Because the company doesn’t own your phone, they can’t ensure it has strong passwords or the latest security updates.
- **Missing Defense:** Personal devices often lack professional-grade **antivirus** or **firewalls**.
- **Data Exposure:** If you lose your personal device, sensitive company files stored on it could be stolen


### 4. Django
Today I finally started to work a bit on the video. Because yesterday I was learning
- WebSockets
- manage.py file
- Commands
- Project Files Explained

Today I discussed with ChatGPT about:
- [[Migrations]]
- [[Migrations commands]]

> Migration
> 	**A set of instructions that tells Django how to change the database.**

#### Migration Commands
- **`python manage.py makemigrations`**
- **`python manage.py migrate


### 5. Python AI Agents
Today I did multiple things. 
I was working on [[Smart File Organizer Agent]].

I asked ChatGPT for more [[Ideas for tools|tools ideas]] and 
##### 1. I imported couple of models
I imported
- `ToolNode` from `langgraph.prebuilt`
- `shutil`
- `time`
- `os`
##### 2. I created multiple tools
I created 4 tools
- `get_file_metadata`
- `move_file`
- `rename_file`
- `create_folder`

More changes are in my [File-Organizer-Agent](https://github.com/TimHuza/File-Organizer-Agent) repository