#journal 


### **1. VS Code Documentation**
Today I did [[Best Practices]] section in Agents section

#### **Important things** from this documentation:

##### **1. Project Configuration and Optimization**
- **Configure your codebase for AI:** Use the `/init` command in chat to generate a starter configuration that helps the AI follow your team's standards.
- **Use specialized mechanisms:** Improve AI accuracy by using **custom instructions** for coding standards, **custom agents** for specific workflows like security audits, and **MCP servers** to connect to external systems like databases.
- **Keep instructions lean:** Focus instruction files on things the AI cannot infer from the code, such as non-default conventions or architectural decisions.
##### **2. Choosing the Right Tools and Agents**
- **Select the appropriate interaction mode:** Use **Inline suggestions** for boilerplate code, **Ask (chat)** for brainstorming, **Plan** for architectural design, and **Overview** for multi-file changes.
- **Match agents to the task:** Use **local agents** for interactive iterations, **background agents** for well-defined tasks you don't need to monitor, and **cloud agents** for team collaboration and pull requests.
##### **3. Effective Prompting and Context**
- **Be specific and structured:** State specific languages and frameworks, break complex tasks into smaller steps, and include expected output for the AI to verify its work.
- **Guide the AI with context:** Use symbols like `#file`, `#folder`, or `#symbol` to point the AI to relevant code, and use `#fetch` to pull information from web pages or GitHub.
- **Iterate and course-correct:** Avoid vague prompts like "make this better" and instead provide specific directions; if the AI goes off track, steer it early with follow-up messages.
##### **4. Workflow and Resource Management**
- **Plan before implementing:** For complex changes, follow a four-step workflow: **Explore** the code, **Plan** the implementation, **Implement** from that plan, and finally **Review** the changes.
- **Review and verify output:** Always treat AI-generated code as a starting point; review it for bugs, run tests, and check for security vulnerabilities before accepting changes.
- **Manage sessions and credits:** Start fresh sessions for unrelated tasks to avoid "context pollution," which reduces response quality and wastes AI credits.
- **Match models to complexity:** Use faster, cheaper models for simple boilerplate and reserve advanced reasoning-optimized models for planning and debugging.
##### **5. Handling Large Codebases**
- **Use indexing:** Leverage workspace indexing and remote indexing for fast results across large enterprise repositories.
- **Scope your work:** Use multi-root workspaces to give the AI clear boundaries and focused context for specific services or modules.


### **2. CyberArk**
Today I did flashcards on Backup and Restore, quiz on Backup and Restore on 8/10, and generated a video for Backup and Restore topic that really helped me for doing this quiz.

![[backup-and-restore-quiz.png]]



### **3. Cyber Security**
Today I did quiz on 54. Stuxnet


### **4. Django**
Today I was doing code with september.
- I created orders
- Users template
- modules.py for orders
- registered them in admin


### **5. AI Projects**
Today I fixed issues and created `fix/errors-fixes` branch for that. Made an issue for this reason closed it. Created pull request and merged it.

Errors:
Fixed multiple type-checking errors in `permission_agent`, `summarize_agent`, and the `create_folder` tool.

---

#### 1. Fixed `permission_agent`

### Problem

The previous implementation tried to access `message_type` from the response object:

```python
return {
    "action": response.message_type
}
```

This caused a type error because the response was being interpreted as a dictionary and did not contain the `message_type` attribute.

### Fix

Replaced the LLM-based decision with a simple keyword-based classifier:

```python
user_message = state["messages"][-1].content.lower()

if "summarize" in user_message:
    action = "summarize"
else:
    action = "organize"

return {
    "action": action
}
```

### Reason

The agent now determines the action using the user's message content instead of relying on an LLM response structure.

---

#### 2. Fixed `summarize_agent`

### Problem

The wrong variable was used when calling the model:

```python
response = SUMMARY_MODEL.invoke(
    prompt
)
```

`SUMMARY_MODEL` contained the model name string instead of the `ChatOllama` instance, causing:

```
Cannot access attribute "invoke" for class "Literal['phi3:mini']"
```

### Fix

Changed it to use the variable containing the actual `ChatOllama` model:

```python
response = summarize_llm.invoke(
    prompt
)
```

### Reason

`invoke()` is a method available on the `ChatOllama` model object, not on a string model name.

---

#### 3. Fixed `create_folder` tool return type issue

### Problem

The function was expected to return a `str`, but some branches returned `None`:

```python
return None
```

This caused:

```
Type "None" is not assignable to return type "str"
```

### Fix

Updated the validation logic so the function keeps the expected string return type:

```python
if not path.exists():
    print(f"❌ File '{file_path}' not found.")
elif not path.is_file():
    print(f"❌ File '{file_path}' is not a file.")
```

### Reason

The function no longer returns `None` in cases where the return type expects a string.

---

## Result

All reported type-checking issues have been resolved:

* ✅ Fixed `permission_agent` response handling
* ✅ Fixed incorrect model variable usage in `summarize_agent`
* ✅ Fixed return type issue in `create_folder` tool