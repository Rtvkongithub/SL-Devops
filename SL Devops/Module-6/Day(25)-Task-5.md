# Git Commands Reference (Days 22–25)

## 1. Setup & Config

### Initialize a Repository
```bash
git init
```

### Clone a Repository
```bash
git clone <repository-url>
```

### Configure Git Username
```bash
git config --global user.name "Your Name"
```

### Configure Git Email
```bash
git config --global user.email "your-email@example.com"
```

### View Configuration
```bash
git config --list
```

---

# 2. Basic Workflow

## Check Repository Status
```bash
git status
```

## Add a Specific File
```bash
git add <file-name>
```

## Add All Files
```bash
git add .
```

## Commit Changes
```bash
git commit -m "Commit message"
```

## View Commit History
```bash
git log
```

## View Compact Commit History
```bash
git log --oneline
```

## View Commit Graph
```bash
git log --oneline --graph --all
```

## View Unstaged Changes
```bash
git diff
```

## View Staged Changes
```bash
git diff --staged
```

---

# 3. Branching

## List Branches
```bash
git branch
```

## Create a New Branch
```bash
git branch feature-login
```

## Create and Switch to a New Branch
```bash
git switch -c feature-login
```

## Switch to an Existing Branch
```bash
git switch main
```

## Switch Branch (Older Command)
```bash
git checkout feature-login
```

## Create and Switch Using checkout
```bash
git checkout -b feature-profile
```

## Delete a Local Branch
```bash
git branch -d feature-login
```

## Force Delete a Branch
```bash
git branch -D feature-login
```

---

# 4. Remote

## View Remote Repositories
```bash
git remote -v
```

## Add a Remote Repository
```bash
git remote add origin <repository-url>
```

## Push to Remote
```bash
git push origin main
```

## Push and Set Upstream Branch
```bash
git push -u origin main
```

## Pull Latest Changes
```bash
git pull
```

## Fetch Latest Changes
```bash
git fetch
```

## Clone a Repository
```bash
git clone <repository-url>
```

## Fork

A **Fork** creates your own copy of someone else's GitHub repository. You can make changes independently and later submit a Pull Request to the original repository.

---

# 5. Merging & Rebasing

## Merge a Branch
```bash
git merge feature-login
```

## Rebase Current Branch onto Main
```bash
git rebase main
```

## Continue Rebase After Resolving Conflicts
```bash
git rebase --continue
```

## Abort Rebase
```bash
git rebase --abort
```

---

# 6. Stash & Cherry-pick

## Save Current Changes
```bash
git stash
```

## View Stash List
```bash
git stash list
```

## Apply Latest Stash
```bash
git stash apply
```

## Apply and Remove Latest Stash
```bash
git stash pop
```

## Delete a Stash
```bash
git stash drop
```

## Apply a Specific Commit
```bash
git cherry-pick <commit-hash>
```

---

# 7. Reset & Revert

## Soft Reset
Removes the latest commit but keeps changes staged.

```bash
git reset --soft HEAD~1
```

## Mixed Reset (Default)
Removes the latest commit and unstages the changes.

```bash
git reset --mixed HEAD~1
```

## Hard Reset
Removes the latest commit and permanently deletes all changes.

```bash
git reset --hard HEAD~1
```

## Revert a Commit
Creates a new commit that reverses the changes of a previous commit.

```bash
git revert <commit-hash>
```

---

# Quick Reference Table

| Command | Description |
|---------|-------------|
| `git init` | Initialize a new Git repository |
| `git clone` | Clone a remote repository |
| `git config --global user.name` | Set Git username |
| `git config --global user.email` | Set Git email |
| `git config --list` | View Git configuration |
| `git status` | Show repository status |
| `git add` | Stage changes |
| `git commit` | Commit staged changes |
| `git log` | View commit history |
| `git log --oneline` | View compact commit history |
| `git log --oneline --graph --all` | View graphical commit history |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git branch` | List or create branches |
| `git switch` | Switch branches |
| `git checkout` | Switch branches or restore files (older command) |
| `git merge` | Merge one branch into another |
| `git rebase` | Reapply commits on top of another branch |
| `git push` | Upload commits to remote repository |
| `git pull` | Fetch and merge remote changes |
| `git fetch` | Download remote changes without merging |
| `git remote -v` | View configured remotes |
| `git stash` | Temporarily save uncommitted changes |
| `git stash pop` | Apply and remove the latest stash |
| `git stash apply` | Apply a stash without removing it |
| `git stash list` | List all stashes |
| `git cherry-pick` | Apply a specific commit to the current branch |
| `git reset --soft` | Undo commit, keep changes staged |
| `git reset --mixed` | Undo commit, keep changes unstaged |
| `git reset --hard` | Undo commit and permanently delete changes |
| `git revert` | Undo a commit by creating a new commit |
