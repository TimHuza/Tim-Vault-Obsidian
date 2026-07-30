#concepts 


**Red, Green, and Refactor subagents** come from the software development practice called **Test-Driven Development (TDD)**.

To understand these subagents, first understand **Red → Green → Refactor**.

---

# What is Red → Green → Refactor?

It is a development cycle:

```
RED
 ↓
GREEN
 ↓
REFACTOR
 ↓
Repeat
```

The idea:

1. **Red** → Write a test that fails.
    
2. **Green** → Write the minimum code needed to make the test pass.
    
3. **Refactor** → Improve the code without breaking the test.
    

---

# What are Red, Green, and Refactor subagents?

They are specialized subagents where each one has a specific responsibility in this cycle.

Think of them as three developers on a team.

```
                 Main Agent
                     |
        ┌────────────┼────────────┐
        |            |            |
   Red Agent    Green Agent  Refactor Agent
   (Testing)    (Coding)     (Improving)
```

---

# 1. Red Subagent 🔴

## Responsibility:

Create tests **before writing the actual feature**.

The Red subagent asks:

> "How do we prove this feature works?"

It creates tests that initially fail.

Example workflow:

You want:

> "Add a function that checks if an answer is correct."

The Red subagent writes:

```python
def test_correct_answer():
    assert check_answer(2 + 2, 4) == True
```

But the function does not exist yet.

Result:

```
❌ Test failed
```

That is why it is called **Red**.

---

# 2. Green Subagent 🟢

## Responsibility:

Make the failing test pass.

The Green subagent asks:

> "What is the simplest code that makes the test pass?"

It writes the implementation:

```python
def check_answer(answer, correct_answer):
    return answer == correct_answer
```

Now:

```
✅ Test passed
```

The goal is not perfect code.

The goal is:

> Make the test green.

---

# 3. Refactor Subagent 🔵

## Responsibility:

Improve the code quality.

The Refactor subagent asks:

> "Can we make this cleaner, faster, or easier to maintain?"

It might:

- Rename variables
    
- Remove duplicate code
    
- Improve structure
    
- Simplify functions
    
- Improve readability
    

Example:

Before:

```python
def check(a,b):
    if a == b:
        return True
    else:
        return False
```

After:

```python
def check_answer(answer, expected):
    return answer == expected
```

The tests should still pass:

```
✅ Tests still pass
```

---

# How the three work together

Imagine you ask:

> "Add a score system to my Python quiz."

The workflow:

```
Main Agent
     |
     |
     ├── Red Subagent
     |       |
     |       Creates tests:
     |       - score increases after correct answer
     |       - score stays after wrong answer
     |
     |
     ├── Green Subagent
     |       |
     |       Writes score system
     |
     |
     └── Refactor Subagent
             |
             Cleans code structure
```

---

# Why split them into subagents?

Because each one thinks differently.

A programmer who writes tests thinks:

> "How can this break?"

A programmer who writes features thinks:

> "How do I make this work?"

A programmer who refactors thinks:

> "How do I make this better?"

Separating these roles reduces mistakes.

---

# Professional software team analogy

Imagine a company:

### 🔴 QA Engineer (Red)

"Before we build this, I will define how we test it."

---

### 🟢 Developer (Green)

"I will write the code to satisfy the tests."

---

### 🔵 Senior Developer (Refactor)

"I will review and improve the implementation."

---

# In VS Code Agents

A professional workflow could be:

```
User Request
      |
      ↓
Main Agent
      |
      ├── Red Subagent
      |     Creates tests
      |
      ├── Green Subagent
      |     Implements feature
      |
      └── Refactor Subagent
            Reviews and improves
```

The important idea:

- **Red = prove the requirement**
    
- **Green = make it work**
    
- **Refactor = make it good**
    

This pattern is one of the most common ways professional developers use multiple agents together.