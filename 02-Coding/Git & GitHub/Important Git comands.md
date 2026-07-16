#git-github

Important **Git** & **GitHub** commands that DevOps developers use everyday.

I'll explain them from the simplest to the more advanced ones.

---

# What is Git?

**Git** is a **version control system**.

# What is GitHub?

Git stores your project **on your computer**.

GitHub stores your Git repository **online**.

<hr>

# 1. `git --version`

Shows your installed Git version.

```bash
git --version
```

Example

```
git version 2.50.1
```

---

# 2. `git config`

Configure Git.

Show all settings

```bash
git config --list
```

Set your name

```bash
git config --global user.name "Tim"
```

Set email

```bash
git config --global user.email "tim@email.com"
```

Why?

Every commit stores

```
Author:
Tim
Email:
tim@email.com
```

---

# 3. `git init`

Creates a Git repository.

```bash
git init
```

Before

```
MyProject/
    app.py
```

After

```
MyProject/
    .git/
    app.py
```

The hidden `.git` folder contains all the history of your project.

---

# 4. `git status`

Probably the most-used Git command.

```bash
git status
```

Example

```
modified: app.py

Untracked files:
README.md
```

It tells you:

- what changed
    
- what Git is tracking
    
- what will be committed
    

---

# 5. `git add`

Moves files into the staging area.

One file

```bash
git add app.py
```

Everything

```bash
git add .
```

Think of it like packing a box before shipping it.

```
Working Directory

↓

git add

↓

Staging Area
```

---

# 6. `git commit`

Creates a snapshot.

```bash
git commit -m "Added login page"
```

Now Git remembers that version forever.

---

# 7. `git log`

Shows commit history.

```bash
git log
```

Example

```
commit 98f32d

Added login

commit a72b1e

Created project
```

Short version

```bash
git log --oneline
```

Output

```
98f32d Added login
a72b1e Created project
```

---

# 8. `git diff`

Shows changes.

```bash
git diff
```

Example

```
-print("Hello")
+print("Hello World")
```

You see exactly what changed.

---

# 9. `git clone`

Downloads an existing repository.

```bash
git clone https://github.com/user/project.git
```

Result

```
GitHub

↓

Downloads

↓

Your Computer
```

---

# 10. `git remote`

Shows connected GitHub repositories.

```bash
git remote -v
```

Example

```
origin
https://github.com/user/project.git
```

---

# 11. `git push`

Uploads commits.

```bash
git push
```

Or

```bash
git push origin main
```

Flow

```
Computer

↓

GitHub
```

---

# 12. `git pull`

Downloads changes.

```bash
git pull
```

Equivalent to

```
git fetch

+

git merge
```

---

# 13. `git fetch`

Downloads updates but doesn't merge them.

```bash
git fetch
```

Safe way to check for updates.

---

# 14. `git branch`

Lists branches.

```bash
git branch
```

Create branch

```bash
git branch feature/login
```

---

# 15. `git switch`

Move between branches.

```bash
git switch feature/login
```

Create and switch

```bash
git switch -c feature/login
```

---

# 16. `git checkout`

Older command.

```bash
git checkout main
```

Also

```bash
git checkout file.py
```

Today, `git switch` and `git restore` are preferred because they're more specific.

---

# 17. `git merge`

Combines branches.

```
main

↓

feature-login

↓

git merge feature-login
```

---

# 18. `git rebase`

Moves commits to another base.

```
Before

A-B-C

    D-E

After rebase

A-B-C-D-E
```

Creates a cleaner history than some merges, but rewrites commit history.

---

# 19. `git stash`

Temporarily saves uncommitted work.

```bash
git stash
```

Restore it

```bash
git stash pop
```

Useful when you need to switch tasks quickly.

---

# 20. `git reset`

Moves the current branch pointer and can unstage or discard changes.

Unstage files:

```bash
git reset
```

Move back one commit but keep changes:

```bash
git reset --soft HEAD~1
```

Discard the last commit and its changes:

```bash
git reset --hard HEAD~1
```

⚠️ `--hard` permanently deletes uncommitted work.

---

# 21. `git restore`

Restore a file.

```bash
git restore app.py
```

Undo staged changes:

```bash
git restore --staged app.py
```

---

# 22. `git rm`

Delete a file and stage the deletion.

```bash
git rm file.txt
```

---

# 23. `git mv`

Rename or move a file while keeping Git history.

```bash
git mv old.py new.py
```

---

# 24. `git tag`

Create a release tag.

```bash
git tag v1.0
```

Used for versions like:

```
v1.0

v2.0

v3.1
```

---

# 25. `git show`

Show details of a commit.

```bash
git show
```

Or

```bash
git show <commit-hash>
```

---

# 26. `git blame`

Shows who changed each line.

```bash
git blame app.py
```

Useful for debugging and understanding code history.

---

# 27. `git cherry-pick`

Copy one specific commit onto another branch.

```bash
git cherry-pick abc1234
```

---

# 28. `git reflog`

Shows every place `HEAD` has pointed recently.

```bash
git reflog
```

A lifesaver if you accidentally reset or delete commits—you can often recover them.

---

# 29. `git clean`

Remove untracked files.

Preview first:

```bash
git clean -n
```

Delete:

```bash
git clean -f
```

---

# 30. `.gitignore`

Not a command, but an essential Git feature.

Example:

```text
venv/
__pycache__/
.env
*.log
```

Git ignores matching files and directories.

---

# 31. `git cherry`

Compare commits between branches.

```bash
git cherry main feature
```

Shows which commits exist on one branch but not the other.

---

# 32. `git bisect`

Helps find the commit that introduced a bug using a binary search.

```bash
git bisect start
git bisect bad
git bisect good <commit>
```

Git checks commits halfway between the good and bad versions until it identifies the problematic commit.

---

# Common GitHub Workflow

A typical day for many DevOps engineers looks like this:

```bash
# Get the latest code
git pull

# Create a new branch
git switch -c feature/add-monitoring

# Check what's changed
git status

# Review your edits
git diff

# Stage your work
git add .

# Save a snapshot
git commit -m "Add Prometheus monitoring"

# Upload your branch
git push origin feature/add-monitoring
```

Then you would open a **Pull Request (PR)** on GitHub, where teammates review your changes before they're merged into the `main` branch.

---

# Commands Used Most Often by DevOps Engineers

These are the commands you'll use constantly:

|Command|Purpose|Frequency|
|---|---|--:|
|`git status`|Check repository state|⭐⭐⭐⭐⭐|
|`git add`|Stage changes|⭐⭐⭐⭐⭐|
|`git commit`|Save changes|⭐⭐⭐⭐⭐|
|`git push`|Upload changes|⭐⭐⭐⭐⭐|
|`git pull`|Get latest changes|⭐⭐⭐⭐⭐|
|`git clone`|Download a repository|⭐⭐⭐⭐⭐|
|`git branch`|Manage branches|⭐⭐⭐⭐|
|`git switch`|Change branches|⭐⭐⭐⭐|
|`git merge`|Combine branches|⭐⭐⭐⭐|
|`git diff`|Review changes|⭐⭐⭐⭐|
|`git log --oneline`|View history|⭐⭐⭐|
|`git fetch`|Retrieve updates|⭐⭐⭐|
|`git stash`|Save work temporarily|⭐⭐⭐|
|`git restore`|Undo file changes|⭐⭐⭐|
|`git reset`|Undo commits or unstage changes|⭐⭐|
|`git rebase`|Rewrite branch history|⭐⭐|
|`git tag`|Mark releases|⭐⭐|
|`git reflog`|Recover lost commits|⭐|
|`git cherry-pick`|Copy a commit|⭐|
|`git bisect`|Find a bug-causing commit|⭐|

If you become comfortable with the first **10–15 commands**, you'll already be able to handle the vast majority of day-to-day Git tasks in a DevOps role. The remaining commands are powerful tools you'll learn as you encounter more advanced workflows.