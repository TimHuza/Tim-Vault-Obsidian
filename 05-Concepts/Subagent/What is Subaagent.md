#concepts 

## Imagine you're building a house

You are the **manager**.

Instead of doing everything yourself, you hire specialists:

- 👷 Electrician → installs the wiring
    
- 🔨 Carpenter → builds the walls
    
- 🚰 Plumber → installs the pipes
    
- 🎨 Painter → paints the rooms
    

Each specialist has **one job** and is good at it.

These specialists are like **subagents**.

---

## What is a subagent?

A **subagent** is a **smaller AI agent that is created by another AI agent to do a specific task**.

Instead of one AI trying to solve everything, it can ask several subagents to work on different parts of the problem.

Think of it like this:

```
Main Agent
     │
     ├── Subagent 1 → Search project files
     ├── Subagent 2 → Write code
     ├── Subagent 3 → Run tests
     └── Subagent 4 → Explain the results
```

The **main agent** is the boss.

The **subagents** are helpers.

---

## A VS Code example

Suppose you tell VS Code:

> "Add a login system to my Django project."

The main agent might decide this is too much work for one agent.

So it creates several subagents.

### Subagent 1

Looks through your project.

> "Where are the models?"

### Subagent 2

Writes the authentication code.

> "I'll add the login logic."

### Subagent 3

Updates the HTML templates.

> "I'll make the login page."

### Subagent 4

Runs the tests.

> "Everything works."

Finally...

The main agent collects all their work and presents the finished result to you.

---

## Another example

Imagine you have a project with **500 Python files**.

If one agent searched them one by one, it could take a while.

Instead:

```
Main Agent

├── Search Agent → looks in Folder A
├── Search Agent → looks in Folder B
├── Search Agent → looks in Folder C
└── Search Agent → looks in Folder D
```

Each subagent searches part of the project at the same time.

This makes the task faster.

---

## Why use subagents?

Subagents help because they can:

- 🚀 Work on multiple tasks at the same time.
    
- 🎯 Focus on one specific job.
    
- 🧠 Use different expertise for different kinds of work.
    
- 📂 Keep complicated tasks organized.
    

It's similar to how a company works:

- The manager plans.
    
- The employees each do one job.
    
- The manager combines everyone's work.
    

---

## A real-life analogy

Imagine your teacher says:

> "Make a presentation about space."

Instead of doing everything yourself:

- Alice researches planets.
    
- Bob finds pictures.
    
- Charlie makes the slides.
    
- You put everything together.
    

Alice, Bob, and Charlie are acting like **subagents**.

You are the **main agent**.

---

## In VS Code

When the documentation talks about **subagents**, it means the main coding agent can automatically create helper agents to perform specialized tasks, such as:

- 🔍 Searching your codebase
    
- 📝 Writing or editing code
    
- 🧪 Running tests
    
- 🐞 Investigating bugs
    
- 📚 Reading documentation
    
- 🔄 Refactoring code
    

The main agent coordinates these helpers and combines their results into one final answer or code change.

## The key idea to remember

Think of it this way:

- **Agent** = the team leader.
    
- **Subagent** = a helper the team leader creates for one specific job.
    
- **Result** = the team leader gathers all the helpers' work and gives you the final solution.
    

So a subagent isn't a completely separate assistant that you chat with directly—it's a helper that the main agent uses behind the scenes to solve complex tasks more efficiently.