#projects

Your `read_files` tool is a good starting point because it gives the agent **information about files**. But for a **Smart File Organizer Agent**, the agent needs more abilities:

- **Observe** → see what files exist
    
- **Understand** → inspect file content/metadata
    
- **Decide** → choose category
    
- **Act** → create folders, rename, move files
    
- **Verify** → check if organization worked
    

Think of tools as the agent's "hands and eyes".

Here are some beginner-friendly tools you can add.

---

# 1. 📂 `list_files` — Scan a folder

### Purpose

Allows the agent to see what files exist in a directory.

### Example

```python
@tool
def list_files(folder_path: str) -> list:
    """
    Lists all files inside a folder.
    """
    import os

    files = []

    for file in os.listdir(folder_path):
        files.append(file)

    return files
```

### Example output

```
[
 "math_homework.pdf",
 "cat_photo.png",
 "main.py",
 "resume.docx"
]
```

### Why useful?

Your agent cannot organize files if it doesn't know what exists.

Workflow:

```
User:
"Organize my Downloads folder"

Agent:
↓
list_files()
↓
Sees 200 files
↓
Processes them
```

---

# 2. 🏷️ `get_file_metadata` — Get file information

Instead of reading every file, get information about it.

Information:

- File type
    
- Size
    
- Creation date
    
- Modification date
    

Example:

```python
@tool
def get_file_metadata(file_path: str):
    """
    Gets metadata about a file.
    """

    import os

    data = {
        "name": os.path.basename(file_path),
        "size": os.path.getsize(file_path),
        "extension": os.path.splitext(file_path)[1],
        "created": os.path.getctime(file_path)
    }

    return data
```

Example:

Input:

```
report.pdf
```

Output:

```json
{
"name":"report.pdf",
"extension":".pdf",
"size":24000
}
```

---

# 3. 🔍 `read_file_content`

Your current tool does this, but I would redesign it.

Currently:

```python
read_files(file_to_read, state, file_contents)
```

Your tool depends on `state` and external variables.

A cleaner agent tool:

```python
@tool
def read_file_content(file_path:str):
    """
    Reads the contents of a file.
    """

    with open(file_path,"r",encoding="utf-8") as f:
        return f.read()
```

Then the agent can do:

```
read_file_content("assignment.txt")

LLM:
"This looks like a school assignment"
```

---

# 4. 🧠 `classify_file`

This is where Ollama becomes useful.

The agent sends information to the LLM.

Example:

```python
@tool
def classify_file(file_name:str, content:str):
    """
    Classifies a file into a category.
    """

    return {
        "category":"School"
    }
```

The LLM decides:

```
math_notes.pdf

↓

Category:
School
```

Possible categories:

```
School
Programming
Images
Documents
Videos
Music
Other
```

---

# 5. 📁 `create_folder`

The agent needs to create folders.

Example:

```python
@tool
def create_folder(folder_name:str):

    import os

    os.makedirs(folder_name, exist_ok=True)

    return f"Folder {folder_name} created"
```

Example:

Agent:

```
Need Programming folder
```

Tool:

```
create_folder("Programming")
```

Result:

```
Downloads/
│
├── Programming/
```

---

# 6. 🚚 `move_file`

This is probably the most important tool.

Example:

```python
@tool
def move_file(source:str, destination:str):
    """
    Moves a file.
    """

    import shutil

    shutil.move(
        source,
        destination
    )

    return "File moved successfully"
```

Example:

Before:

```
Downloads/

math.pdf
main.py
cat.png
```

Agent:

```
math.pdf → School
main.py → Programming
cat.png → Images
```

After:

```
Downloads/

├── School
│    └── math.pdf
│
├── Programming
│    └── main.py
│
└── Images
     └── cat.png
```

---

# 7. ✏️ `rename_file`

Useful because messy names are common.

Example:

Before:

```
IMG_39482.png
```

Agent:

```
This is a vacation picture
```

Rename:

```
Vacation_Beach_2026.png
```

Tool:

```python
@tool
def rename_file(old_name,new_name):

    import os

    os.rename(
        old_name,
        new_name
    )

    return "Renamed"
```

---

# 8. 🗑️ `delete_file`

Useful for duplicates or temporary files.

Example:

```
file.tmp
desktop.ini
old_backup.zip
```

Agent:

```
Temporary files detected
```

Tool:

```python
@tool
def delete_file(file_path):

    import os

    os.remove(file_path)

    return "Deleted"
```

⚠️ For safety, add confirmation:

```
Agent:
"I found 5 temporary files. Delete them?"

User:
"Yes"
```

---

# 9. 🔎 `search_files`

The agent can find files.

Example:

User:

```
Find all Python projects
```

Tool:

```python
@tool
def search_files(extension:str):

    import os

    results=[]

    for root,dirs,files in os.walk("."):
        for file in files:
            if file.endswith(extension):
                results.append(file)

    return results
```

Output:

```
[
main.py,
agent.py,
app.py
]
```

---

# 10. 📊 `generate_report`

Very useful for agents.

After organizing:

```
Organization Report:

Files scanned:
150

Moved:

School:
35 files

Images:
50 files

Programming:
25 files

Skipped:
10 files
```

Tool:

```python
@tool
def generate_report(actions:list):

    return {
        "total_files":len(actions),
        "actions":actions
    }
```

---

# Beginner Version Architecture

I would build your agent like this:

```
                User
                 |
                 |
              LangGraph
                 |
        -------------------
        |                 |
       LLM              Tools
        |                 |
    Ollama          ---------------
                   |
        -----------------------------
        |       |        |           |
    list_files  read   classify   move
              metadata             |
                                   |
                              create_folder
```

---

# Suggested Tool Progression

Don't build all 10 immediately.

I would do:

## Version 1 (Beginner)

Tools:

```
1. list_files
2. get_file_metadata
3. classify_file
4. move_file
```

Your agent can already:

```
Scan Downloads
↓
Understand files
↓
Categorize
↓
Move files
```

---

## Version 2

Add:

```
5. create_folder
6. rename_file
7. generate_report
```

Now it feels like a real AI agent.

---

## Version 3 (Advanced)

Add:

```
8. duplicate_detector
9. file_search
10. undo_changes
11. human_confirmation
```

---

A very nice LangGraph workflow for this project would be:

```
START

 ↓

Scan Folder Node

 ↓

Analyze File Node

 ↓

LLM Decision Node
(Category?)

 ↓

Tool Node
(create folder / move file)

 ↓

Next File?

 ├── Yes → Analyze next file
 |
 └── No

 ↓

Report Node

 ↓

END
```

This project is actually a very good beginner LangGraph project because it naturally teaches **agent loops, tools, state, decisions, and human approval workflows**.