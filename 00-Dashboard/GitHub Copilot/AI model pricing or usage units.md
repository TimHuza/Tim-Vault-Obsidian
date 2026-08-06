
![[credit-usage.png]]





The screenshot shows **AI model pricing/usage units**. These numbers describe how many **credits/tokens are consumed** when you use an AI model (for example through GitHub Copilot's models).

The important idea:

> **Tokens = pieces of text the AI reads and writes.**  
> Your Copilot usage is measured by how much text goes **into** the model and how much text comes **out**.

Your screenshot:

| Type | Cost per 1 million tokens |
|---|---:|
| Input | 300 credits |
| Output | 1500 credits |
| Cache Read | 30 credits |
| Cache Write | 375 credits |

Let's explain each one.

---

## 1. Input tokens (what you send to the AI)

**Input = everything the AI receives from you.**

Examples:

You ask Copilot:

> "Explain this Django model"

Your input includes:

- Your question
- Your code
- Your project context
- Files Copilot reads
- Previous chat messages

Example:

```
User:
Explain this code:

class Product(models.Model):
    name = models.CharField(max_length=100)
```

The model receives maybe:

```
Explain this code:
class Product(models.Model):
    name = models.CharField(max_length=100)
```

That is **input tokens**.

The cost:

```
1 million input tokens = 300 credits
```

Input is usually cheaper because the AI only needs to read.

---

# 2. Output tokens (what the AI generates)

**Output = the answer the AI creates.**

Example:

You ask:

> Explain Django models

Copilot generates:

```
A Django model represents a database table.
The class Product inherits from models.Model...
```

Every word it generates is output tokens.

The cost:

```
1 million output tokens = 1500 credits
```

Output is usually more expensive because generating text requires more computation.

---

# 3. Cache Read tokens

This is a performance optimization.

Imagine you are working on a Django project.

You have:

```
models.py
views.py
forms.py
templates/
settings.py
```

Copilot already analyzed some of your project context.

Instead of sending everything again:

```
models.py
views.py
settings.py
...
```

GitHub can reuse previously processed information.

That reused information is a **cache read**.

Example:

First request:

```
Read:
models.py
views.py
settings.py

Cost:
Input tokens
Cache write
```

Second request:

```
Use the same project information again

Cost:
Cache read (much cheaper)
```

Your screenshot:

```
Cache Read = 30 credits
```

This is much cheaper than normal input:

```
Input = 300 credits
Cache Read = 30 credits
```

So cached information costs about **10 times less**.

---

# 4. Cache Write tokens

This happens when the AI stores information for reuse.

Example:

You open a Django project.

Copilot analyzes:

```
models.py
urls.py
views.py
settings.py
```

and creates cached information.

That storing process is:

```
Cache Write
```

Your screenshot:

```
Cache Write = 375 credits
```

It costs slightly more than input because the system needs to process and store the information.

---

# How does this affect your GitHub Copilot Pro $10 plan?

This is the important part:

## GitHub Copilot Pro is NOT normally like an API account

When you buy:

```
GitHub Copilot Pro
$10/month
```

you usually get:

- Copilot Chat
- Code completion
- Agent features
- Access to supported models
- A monthly allowance of premium requests

You are **not directly paying these token prices yourself** like using OpenAI API.

These numbers are usually showing:

- model cost comparison
- premium request consumption
- internal credit calculations

---

## What actually affects your Copilot Pro usage?

Mostly:

### 1. Which model you choose

Example:

A smaller model:

```
GPT-4.1 mini
```

uses fewer credits.

A larger model:

```
Claude Sonnet
GPT-5
Claude Opus
```

uses more.

---

### 2. How much context you give Copilot

Small question:

```
Explain this function
```

uses little.

Large request:

```
Analyze my entire Django project and redesign the architecture
```

uses much more.

Because Copilot has to read:

```
models.py
views.py
urls.py
settings.py
templates
```

---

### 3. Agent mode uses more

For example:

Normal chat:

```
You:
Explain this error

Copilot:
Here is the explanation
```

Low usage.

Agent:

```
Analyze project
Find files
Modify code
Run tests
Fix errors
```

Higher usage because it:

- reads many files
- reasons multiple times
- generates more output

---

## Example with your Django Teacher Agent idea

You mentioned you want to use Copilot as a **Django Teacher Agent**.

### Cheap usage:

You ask:

```
What is csrf_token?
```

Tokens:

```
Input:
small

Output:
small
```

Very little usage.

---

### More expensive:

You ask:

```
Analyze my entire Django ecommerce project.
Explain the architecture.
Find security problems.
Suggest improvements.
```

Copilot might read:

```
models.py
views.py
forms.py
urls.py
settings.py
templates
```

Tokens:

```
Input: high
Output: high
Cache: maybe used
```

More premium usage.

---

# Simple analogy

Imagine Copilot is a teacher.

| Type | Meaning |
|-|-|
| Input | Pages you give the teacher to read |
| Output | Pages of explanation the teacher writes |
| Cache Read | Teacher remembers previous lessons |
| Cache Write | Teacher takes notes for future lessons |

---

For your **$10 Copilot Pro**, the practical advice is:

✅ Use larger models when you need deep explanations/debugging  
✅ Use smaller models for simple questions/code completion  
✅ Avoid asking Agent mode to scan your entire project unnecessarily  
✅ Let caching help by keeping the same workspace open 