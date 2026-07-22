#git-github 

Since you're a beginner, let's imagine a **Git repository** is a **school notebook**.

- The **main branch** is the **final version** of your homework.
    
- A **branch** is a **photocopy** of your notebook where you can safely experiment.
    
- If you make mistakes on the copy, your original notebook is still safe.
    

This is exactly why developers use multiple branches.

---

# Why do we need more than one branch?

Imagine you're building a website.

Today your project looks like this:

```
main
│
├── index.html
├── styles.css
└── app.js
```

Everything works.

Now your boss says:

> "Add a Login page."

Should you start editing `main` immediately?

**No!**

Why?

Because while you're working:

- the login might not work yet
    
- you might accidentally break the website
    
- other developers still need the working version
    

Instead, you create another branch.

```
main
 │
 └─────────── login-feature
```

Now you work safely on `login-feature`.

---

# What is a branch?

A branch is simply another timeline of your project.

Imagine time looks like this:

```
main

A ---- B ---- C
```

Each letter is a commit.

Now you create a branch.

```
main

A ---- B ---- C
              \
               D
                \
                 E

login-feature
```

Both branches started from commit **C**.

Now:

- `main` stays unchanged
    
- `login-feature` gets new commits
    

---

# Step 1 - Create a branch

You are currently on `main`.

```
main

A ---- B ---- C
```

Create a branch:

```bash
git branch login-feature
```

Now Git creates:

```
main
login-feature

A ---- B ---- C
```

Notice:

Both branches point to the same commit.

Nothing has changed yet.

---

# Step 2 - Switch to the branch

Move onto it:

```bash
git checkout login-feature
```

or the newer command

```bash
git switch login-feature
```

Now you're working here:

```
main

A ---- B ---- C
               ↑
          login-feature
```

Every change you make now belongs to this branch.

---

# Step 3 - Make changes

Suppose you add:

```
login.html
```

Then commit.

```
git add .
git commit -m "Create login page"
```

Now history becomes

```
main

A ---- B ---- C


login-feature

A ---- B ---- C ---- D
```

Only `login-feature` has commit D.

`main` doesn't know it exists.

---

# Step 4 - Continue working

You keep coding.

```
git commit
git commit
git commit
```

History becomes

```
main

A ---- B ---- C


login-feature

A ---- B ---- C ---- D ---- E ---- F
```

Everything is isolated.

---

# Step 5 - Switch back to main

```bash
git switch main
```

Now your project instantly changes.

You no longer see your login page.

Your files become exactly what they were on `main`.

```
main

A ---- B ---- C
```

This surprises many beginners.

Git actually changes the files on your computer to match the selected branch.

---

# Working on another feature

Now your boss says:

> "Fix the navigation menu."

Don't use the login branch.

Create another branch.

```
main

A ---- B ---- C
 \
  \
   navigation-fix
```

Now you have

```
main

login-feature

navigation-fix
```

Each branch is independent.

---

# Real developer workflow

Suppose a website needs three new features.

```
Website

main
```

Developer 1

```
main
   \
    login-feature
```

Developer 2

```
main
   \
    payment-feature
```

Developer 3

```
main
   \
    dark-mode
```

Everyone works separately.

Nobody breaks anyone else's work.

---

# Typical commands

## See all branches

```bash
git branch
```

Output:

```text
* main
  login-feature
  dark-mode
```

The `*` means:

> You are currently on `main`.

---

## Create a branch

```bash
git branch login-feature
```

---

## Switch branches

```bash
git switch login-feature
```

or

```bash
git checkout login-feature
```

---

## Create and switch at the same time

```bash
git switch -c login-feature
```

Older version:

```bash
git checkout -b login-feature
```

---

## Delete a branch

After the work has been merged into `main`:

```bash
git branch -d login-feature
```

---

# A complete example

Start:

```
main

A
```

Create a branch.

```
main

A
 \
  login
```

Commit twice.

```
main

A

login

A ---- B ---- C
```

Go back to main.

```
main

A
```

Main still doesn't have the login feature.

When the login feature is finished, you merge it into `main` (we'll cover merging in more detail separately).

```
Before merge

main

A

login

A ---- B ---- C
```

After merge

```
main

A ---- B ---- C

login

A ---- B ---- C
```

Now both branches contain the completed work.

---

# The workflow developers use every day

Whenever a new task comes in:

1. Go to `main`
    
2. Make sure it's up to date
    
3. Create a new branch
    
4. Work only in that branch
    
5. Commit your changes
    
6. Push the branch to GitHub
    
7. Open a Pull Request
    
8. Merge into `main`
    
9. Delete the branch
    

This keeps the `main` branch stable and lets multiple developers work on different tasks without interfering with each other.

## Example

Imagine you're building a game with three tasks:

```
main
│
├── Hero works
├── Enemy works
└── Menu works
```

Create one branch for each task:

```
main
│
├── feature/jump
├── feature/inventory
└── bugfix/menu
```

Each branch focuses on **one specific change**. When a feature is finished and reviewed, it's merged back into `main`.

As a beginner, this is the workflow you'll see in most professional software teams. Once you're comfortable with creating, switching, and deleting branches, the next important concept to learn is **merging**, because that's how work from different branches is combined back into `main`.