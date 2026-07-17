#git-github 


> **A Pull Request is NOT a Git feature.**

It is a **GitHub feature** (also available in GitLab as Merge Requests and in Azure DevOps as Pull Requests).

Git handles commits and branches.  
GitHub adds collaboration tools on top of Git.

---

# What is a Pull Request?

A **Pull Request (PR)** is a request to merge one branch into another.

Think of it as saying:

> "I've finished my work. Could someone review it before we merge it into the project?"

It does **not** merge automatically.

Someone (or you) must approve it.

---

# Real-world analogy

Imagine you're writing a textbook with a team.

Instead of editing the official version directly, you:

1. Copy the book.
    
2. Make your changes.
    
3. Hand it to the editor.
    

The editor then:

- reads your changes
    
- leaves comments
    
- requests fixes
    
- approves them
    
- merges them into the official book
    

A Pull Request is that review process.

---

# Why not just merge directly?

Imagine five developers.

```text
Developer A
Developer B
Developer C
Developer D
Developer E
```

If everyone merged directly into `main`:

```text
main

A
B
C
D
E
```

Problems:

- bugs
    
- broken builds
    
- unreadable code
    
- accidental deletions
    

Instead everyone creates a PR first.

---

# Complete workflow

Suppose you start with

```text
main

A --- B
```

---

## Step 1: Create a branch

```bash
git checkout -b login-page
```

Now

```text
main

A --- B
         \
login-page
```

---

## Step 2: Write code

You work for several hours.

```bash
git add .
git commit -m "Create login page"

git add .
git commit -m "Add validation"
```

History

```text
main

A --- B
         \
login-page
          \
           C --- D
```

---

## Step 3: Push branch to GitHub

```bash
git push origin login-page
```

Now GitHub knows your branch exists.

Repository:

```text
GitHub

main

A --- B

login-page

A --- B --- C --- D
```

Nothing has been merged yet.

---

# Step 4: Open Pull Request

On GitHub you'll see

```text
Compare & pull request
```

Click it.

GitHub asks

```text
Base branch:
main

Compare branch:
login-page
```

Meaning:

> Merge **login-page** INTO **main**

Not the other way around.

---

# GitHub compares branches

GitHub now calculates

```text
main

A --- B

feature

A --- B --- C --- D
```

GitHub notices

Feature has

- commit C
    
- commit D
    

It shows only those changes.

---

# What reviewers see

Instead of reviewing the whole project, they only review the differences.

Example

Old code

```python
print("Hello")
```

New code

```python
print("Hello Tim")
```

GitHub highlights

```diff
- print("Hello")
+ print("Hello Tim")
```

Only the changed lines.

This is called a **diff**.

---

# Code Review

Now another developer reads your code.

They may comment

```text
Can you rename this variable?
```

or

```text
This function is too long.
```

or

```text
Great work!
```

You don't need to create another PR.

Simply make more commits.

```bash
git add .
git commit -m "Rename variable"
git push
```

GitHub automatically updates the existing PR.

---

# CI/CD runs automatically

Many companies connect GitHub with automation tools like GitHub Actions, Jenkins, or Azure DevOps.

As soon as you open a PR:

```text
Pull Request

↓

Run tests

↓

Run linter

↓

Build project

↓

Security scan

↓

Deploy preview (optional)
```

If anything fails

```text
❌ Tests failed
```

You usually cannot merge until it's fixed.

---

# Approval

Once reviewers are happy

```text
✅ Approved
```

Now the Merge button becomes available.

---

# Merge Pull Request

Click

```text
Merge Pull Request
```

GitHub performs the merge for you.

History becomes

```text
A --- B -------- M
       \        /
        C ---- D
```

Exactly like the Git merge you learned previously.

GitHub is simply performing:

```bash
git checkout main
git merge login-page
```

behind the scenes.

---

# Delete branch

After merging

GitHub usually asks

```text
Delete branch
```

Why?

Because

```text
login-page
```

is finished.

Your history becomes

```text
main

A --- B --- M
```

The commits remain.

Only the branch pointer disappears.

---

# Three merge options on GitHub

When merging a PR, GitHub usually offers three choices.

## 1. Create a Merge Commit (default)

```text
A --- B ------- M
       \       /
        C --- D
```

Preserves the branch history.

Most common in large teams.

---

## 2. Squash and Merge

Instead of

```text
C
D
E
F
```

GitHub creates

```text
A --- B --- G
```

where **G** contains all the changes from C, D, E, and F combined into a single commit.

This keeps `main`'s history cleaner.

---

## 3. Rebase and Merge

Instead of creating a merge commit, GitHub rewrites the branch history so it looks like the feature branch was created from the latest `main`.

Before:

```text
A --- B
       \
        C --- D
```

After rebasing and merging:

```text
A --- B --- C --- D
```

No merge commit is created, resulting in a linear history. This is useful but more advanced because rebasing rewrites commit history.

---

# Typical workflow in a company

```text
Pull latest code

↓

Create feature branch

↓

Write code

↓

Commit

↓

Push

↓

Open Pull Request

↓

CI/CD runs

↓

Code Review

↓

Fix comments

↓

Approve

↓

Merge

↓

Delete branch
```

---

# Example with actual commands

### Create a branch

```bash
git checkout -b login-page
```

---

### Work

```bash
git add .
git commit -m "Create login page"
```

---

### Push

```bash
git push -u origin login-page
```

---

### Open PR

On GitHub:

```text
Compare & Pull Request
```

---

### Reviewer comments

You fix the code.

```bash
git add .
git commit -m "Fix review comments"
git push
```

The PR updates automatically.

---

### Merge

Click

```text
Merge Pull Request
```

---

### Delete branch

```bash
git branch -d login-page
```

---

# Visual summary

```text
main

A ---- B
         \
feature   C ---- D
             |
             | Push
             ▼
        GitHub Pull Request
             |
             ▼
      Code Review + Tests
             |
      ┌──────┴──────┐
      │             │
   Changes       Approved
      │             │
      └──────┬──────┘
             ▼
        Merge into main
             ▼
A ---- B -------- M
       \        /
        C ---- D
```

## Beginner tip

As you're learning Git, here's a simple rule to remember:

- **Git** manages your local repository: branches, commits, merges, etc.
    
- **GitHub** is where you share that repository with others and collaborate.
    
- A **Pull Request** is simply GitHub's way of saying, "Please review my branch before we merge it."
    

Once you're comfortable with Pull Requests, the next concepts to learn are **merge conflicts inside a PR**, **GitHub Actions (CI/CD)**, and **fork-based Pull Requests** (used when contributing to open-source projects). These are common parts of professional development workflows.