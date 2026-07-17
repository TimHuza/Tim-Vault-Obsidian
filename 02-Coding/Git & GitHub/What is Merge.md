#git-github 

# What is a merge?

A **merge** is the process of **combining the history of two branches into one**.

Think of branches as separate timelines.

```
main

A --- B --- C
```

You create a new feature branch.

```
main

A --- B --- C
             \
feature       D --- E
```

Now you have two separate histories.

- `main` still ends at **C**
    
- `feature` has two extra commits **D** and **E**
    

Eventually your feature is finished.

Now you want those commits on `main`.

That's what **merge** does.

---

# Real-life analogy

Imagine two writers editing the same book.

### Main book

```
Chapter 1
Chapter 2
Chapter 3
```

Your friend makes edits in another copy.

```
Chapter 1
Chapter 2
Chapter 3
Chapter 4
```

Eventually they say

> "I'm done. Put my changes into the official book."

That is exactly what a Git merge does.

---

# How merge works

Suppose you have

```
main

A --- B --- C

feature

A --- B --- C --- D --- E
```

Notice both branches share history until **C**.

Git finds the **common ancestor**.

```
A --- B --- C
```

Then Git asks:

> "What changed after C?"

Answer:

Feature added

```
D
E
```

Git applies those changes onto `main`.

Result:

```
A --- B --- C -------- M
             \        /
              D ---- E
```

Notice something new appeared.

```
M
```

That is called a **merge commit**.

---

# What is a merge commit?

A normal commit has **one parent**.

```
A --> B --> C
```

Commit C only knows about B.

A merge commit has **two parents**.

```
      D --- E
     /       \
A -- B -- C -- M
```

Merge commit **M** says

"I came from BOTH branches."

---

# Example

Start here

```
main

A --- B
```

Create feature branch

```bash
git checkout -b feature
```

Now

```
main

A --- B
         \
feature
```

Make changes

```
main

A --- B
         \
feature    C --- D
```

Go back

```bash
git checkout main
```

Merge

```bash
git merge feature
```

Result

```
A --- B ------- M
       \       /
        C --- D
```

Now both branches contain the feature.

---

# What command do developers use?

Suppose

```
main

A --- B

feature

A --- B --- C --- D
```

Switch to the branch that should receive changes.

```bash
git checkout main
```

Merge

```bash
git merge feature
```

Git combines them.

---

# Why do we merge into main?

Because `main` is usually the production branch.

Typical workflow:

```
main

↓

Create feature branch

↓

Work

↓

Commit

↓

Merge back

↓

Delete feature branch
```

---

# Complete developer workflow

## Step 1

Clone repository

```bash
git clone <repo>
```

---

## Step 2

Create branch

```bash
git checkout -b login-page
```

Now

```
main

A --- B
         \
login-page
```

---

## Step 3

Work

```bash
git add .
git commit -m "Create login page"
```

```
main

A --- B
         \
login-page
          \
           C
```

---

## Step 4

More work

```bash
git commit -m "Add validation"
```

```
main

A --- B
         \
login-page
          \
           C --- D
```

---

## Step 5

Switch back

```bash
git checkout main
```

---

## Step 6

Merge

```bash
git merge login-page
```

```
A --- B -------- M
       \        /
        C ---- D
```

Done.

---

# Fast-forward merge

Sometimes Git doesn't even create a merge commit.

Example

```
main

A --- B

feature

A --- B --- C --- D
```

Nobody touched `main`.

Git notices

> "I don't need a merge commit."

It simply moves `main` forward.

Before

```
main
 ↓

A --- B

feature
        ↓

A --- B --- C --- D
```

After

```
main
feature
          ↓

A --- B --- C --- D
```

This is called a **fast-forward merge**.

No merge commit is created.

---

# Three-way merge

Now suppose both branches changed.

```
main

A --- B --- C

feature

A --- B --- D --- E
```

Git can't simply move the pointer.

Instead it creates

```
A --- B --- C -------- M
         \            /
          D -------- E
```

This is called a **three-way merge**.

Git compares

- common ancestor
    
- main
    
- feature
    

Then combines them.

---

# What is a merge conflict?

This is the scary part beginners hear about.

Imagine

Original file

```python
name = "Tim"
```

On `main` someone changes it

```python
name = "John"
```

On your feature branch you change it

```python
name = "Alice"
```

Git asks

> "Which one should I keep?"

It can't decide.

So it creates a conflict.

```
<<<<<<< HEAD
name = "John"
=======
name = "Alice"
>>>>>>> feature
```

You must edit it manually.

Maybe

```python
name = "John and Alice"
```

or

```python
name = "Alice"
```

Then

```bash
git add .
git commit
```

Conflict solved.

---

# How developers usually work

A developer rarely works directly on `main`.

Instead

```
main

↓

Create branch

↓

Write code

↓

Commit often

↓

Push branch

↓

Open Pull Request

↓

Code Review

↓

Merge into main
```

This keeps `main` stable.

---

# Visual summary

```
1. Start

A --- B
        main
```

```
2. Create branch

A --- B
        \
         feature
```

```
3. Work

A --- B
        \
         C --- D
```

```
4. Merge

A --- B -------- M
       \        /
        C ---- D
```

---

# Best practices

As a developer, it's a good habit to:

- **Create a new branch for every feature or bug fix.**
    
- **Commit small, meaningful changes** instead of one huge commit.
    
- **Keep your feature branch updated** by bringing in the latest `main` changes if your work lasts several days.
    
- **Merge only after testing** your code.
    
- **Delete merged feature branches** once they're no longer needed.
    

---

## The three merge commands you'll use most

```bash
# Switch to the branch that should receive changes
git checkout main

# Merge another branch into it
git merge feature-branch

# Delete the merged branch (optional but common)
git branch -d feature-branch
```

---

As you continue learning Git, the next concepts that naturally build on merges are:

1. **Merge conflicts** (how to resolve them step by step)
    
2. **Rebase** (another way to combine branches, often used to keep history clean)
    
3. **Pull Requests (PRs)** on GitHub, where merges typically happen in team projects.
    

Understanding those three topics will give you the complete picture of how professional developers collaborate with Git and GitHub.