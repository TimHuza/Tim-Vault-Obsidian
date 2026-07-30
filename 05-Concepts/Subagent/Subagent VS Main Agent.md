#concepts 


> **The main agent is the boss. A subagent is a helper hired by the boss to do one specific job.**

Here's a comparison:

|Main Agent|Subagent|
|---|---|
|🧠 Controls the entire task|🎯 Handles one specific task|
|👤 Talks directly to you|🤖 Usually works behind the scenes|
|📋 Makes the overall plan|📋 Follows the plan given by the main agent|
|📦 Combines all results|📦 Returns its result to the main agent|
|🏁 Delivers the final answer|🔧 Does part of the work|

---

## Example 1: Fixing a bug

You ask VS Code:

> "Find and fix the bug causing my Django app to crash."

### Without subagents

One agent does everything:

```
Main Agent

1. Search files
2. Read code
3. Find bug
4. Fix bug
5. Run tests
6. Explain changes
```

This works, but it may take longer because it's doing each step itself.

---

### With subagents

The main agent becomes the project manager.

```
                Main Agent
                     │
      ┌──────────────┼──────────────┐
      │              │              │
 Search Agent   Bug Analysis    Test Agent
   (finds         (finds          (runs
   files)          problem)       tests)
      │              │              │
      └──────────────┼──────────────┘
                     │
             Main Agent
        combines everything
```

The main agent doesn't do every piece itself—it coordinates the work.

---

## Example 2: Adding a feature

Suppose you ask:

> "Add a shopping cart to my website."

The main agent might create subagents like this:

### Main Agent

"I need several things done."

↓

### Subagent 1

"I'll create the database models."

↓

### Subagent 2

"I'll update the views."

↓

### Subagent 3

"I'll edit the HTML templates."

↓

### Subagent 4

"I'll write tests."

↓

### Main Agent

"Great! I'll combine everyone's work and show it to the user."

---

## Think of a restaurant 🍕

### Main Agent = Restaurant Manager

The manager:

- Greets customers
    
- Takes the order
    
- Decides who does what
    
- Checks the food
    
- Gives the meal to the customer
    

---

### Subagents = Restaurant Staff

One cook:

> Makes the pizza.

Another cook:

> Makes the salad.

Someone else:

> Prepares drinks.

A server:

> Brings everything to the table.

The customer only talks to the **manager**, even though many people helped prepare the meal.

---

## In VS Code

When you type a request into Chat:

```
"Refactor my project."
```

You are talking to the **main agent**.

The main agent may decide:

- "I'll ask one helper to search the project."
    
- "I'll ask another helper to rewrite the code."
    
- "I'll ask another helper to run tests."
    

When they're finished, the main agent combines everything and responds to you.

---

## A simple analogy

Imagine you're doing a school group project.

### Main Agent = Team Leader

- Understands the assignment
    
- Divides the work
    
- Collects everyone's part
    
- Submits the final project
    

### Subagents = Team Members

- One researches
    
- One writes
    
- One finds pictures
    
- One checks spelling
    

The teacher only receives **one final project**, even though several people contributed.

## The biggest difference

- **Main agent:** Thinks about the entire problem, decides what needs to happen, coordinates the work, and gives you the final result.
    
- **Subagent:** Focuses on a single assigned task and reports back to the main agent. It doesn't usually interact with you directly.