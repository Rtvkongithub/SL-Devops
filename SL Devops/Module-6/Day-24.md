# Advanced Git: Merge, Rebase, Stash & Cherry Pick

## Task - 1
<img width="1022" height="573" alt="image" src="https://github.com/user-
attachments/assets/a073dded-96ab-4b77-acf6-a5de9891e51a" />
<img width="1157" height="721" alt="image" src="https://github.com/user-attachments/assets/d7bb7491-a6da-4f86-a6f4-3aad03001fbf" />

### Merge Conflict
- Created `feature-conflict` branch.
- Added `conflict.txt`.
- Modified `conflict.txt` differently in both `master` and `feature-conflict`.
- Merged `feature-conflict` into `master`.
- Git reported:
- Resolved the conflict manually.
- Ran:
```
git add conflict.txt
git commit -m "Resolve merge conflict"
```
## What is a merge conflict?
A merge conflict happens when Git cannot automatically combine changes, usually because the same line was modified in both branches.
<img width="1702" height="171" alt="image" src="https://github.com/user-attachments/assets/986b0302-af4c-4086-8027-12d4441f732d" />


## Task - 2
- git switch -c feature-dashboard 
-  echo "Dashboard UI" > dashboard.txt
-   git add dashboard.txt
-  git commit -m "Dashboard UI"
-  echo "Dashboard API" >> dashboard.txt
-  git add dashboard.txt
-  git commit -m "Dashboard API"
-  git switch master
-  echo "Footer" > footer.txt
-  git add footer.txt
-  git commit -m "Add footer"
-  git switch feature-dashboard
-  git rebase main
-  git rebase master 
-  git log --oneline --graph --all
### What does rebase do?

Rebase moves your commits on top of another branch, creating a linear history.

------------------------------------------------

### How is history different from merge?

Merge keeps branch history with merge commits.

Rebase rewrites history into a straight line.

------------------------------------------------

### Why should you never rebase shared commits?

Rebasing changes commit hashes, causing problems for others who already pulled those commits.

------------------------------------------------

### When would you use rebase vs merge?

Use rebase before sharing to keep history clean.

Use merge when combining completed work without changing history.

<img width="1702" height="388" alt="image" src="https://github.com/user-attachments/assets/c4d568d5-74b9-4978-91db-991537f4f9ba" />

## Task - 3
<img width="1180" height="573" alt="image" src="https://github.com/user-attachments/assets/a0e7da40-2d18-4ef1-baa9-08b7986cec33" />

### Squash Merge

#### What does squash merging do?

where G contains all the changes from C, D, E, and F as one commit.

It combines multiple commits into one before merging.

------------------------------------------------

#### When would you use squash merge?

When a feature has many small commits and you want a clean history.

------------------------------------------------

#### Trade-off

You lose the detailed commit history inside that feature branch.

## Task - 4

git switch master
<img width="1902" height="572" alt="image" src="https://github.com/user-attachments/assets/9acb2cb4-06db-4917-8b48-8c77b4445871" />

switching branches

if it says "Your local changes would be overwritten..." / must stash
```
git stash or git stash push -m "Working on git commands"
```
git status => Your changes disappeared but are safely stored.
<img width="1115" height="736" alt="image" src="https://github.com/user-attachments/assets/ce9af9bd-4424-4d76-8db3-86ff4f5d0663" />
<img width="1115" height="736" alt="image" src="https://github.com/user-attachments/assets/44aa7cd6-4e24-4146-bce8-c4c83836ae0d" />

- Multiple stashes
```
echo "Another line" >> git-commands.md

git stash push -m "Second work"

echo "Third line" >> git-commands.md

git stash push -m "Third work"

git stash list

Output

stash@{0}
stash@{1}

Apply only one
git stash apply stash@{1}

Notice it is still in the stash list.
If you use

git stash pop

Git restores it and removes it from the list.
```

## Task - 5 cheryy picking

```
git switch -c feature-hotfix

echo "Bug 1" > bugfix.txt
git add bugfix.txt
git commit -m "Hotfix 1"

echo "Bug 2" >> bugfix.txt
git add bugfix.txt
git commit -m "Hotfix 2"

echo "Bug 3" >> bugfix.txt
git add bugfix.txt
git commit -m "Hotfix 3"

git switch master
git cherry-pick <hash-of-Hotfix-2>
```

if conflicts come 
- start from first 
- Either add (hotfix) & git cherry-pick --continue
- if its not seen
<img width="1093" height="562" alt="image" src="https://github.com/user-attachments/assets/d591fdf4-b0ee-4ab5-92b6-ce7d439f3ef3" />
