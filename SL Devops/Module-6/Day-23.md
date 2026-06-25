# Task - 1
## What is a branch in Git?
A branch is an independent line of development. It lets you work on new features or fixes without affecting the main branch.

------------------------------------------------

## Why do we use branches instead of committing everything to main?

Branches keep the main branch stable. Developers can work on new features, bug fixes, or experiments separately and merge them later.

------------------------------------------------

## What is HEAD in Git?

HEAD is a pointer to the current branch or the latest commit you are working on.

------------------------------------------------

## What happens to your files when you switch branches?

Git changes your working directory to match the selected branch. Files that exist only in one branch will appear or disappear accordingly.

# Task - 2

Notes i done 
<img width="1920" height="986" alt="image" src="https://github.com/user-attachments/assets/5763dd99-5275-4939-ba8e-1aeca4745d3e" />
<img width="1920" height="320" alt="image" src="https://github.com/user-attachments/assets/ab4cbc0a-daae-4a35-a77f-06b9fadd3c89" />
```
git branch
git branch feature -1
git checkout feature -1
git switch feature -1
git switch -c feature -2

# switch -> mainly for the branch
# checkout -> to create, restore, switch

git switch feature-1
echo "hai" >> hai.txt/git add hai.txt/ git commit -m "adding"
git switch master
git ls

git branch -d feature -1
```
# Task 3: Push to GitHub
```
git remote add origin https://github.com/Rtvkongithub/devops-git-practice.git
git push origin main
```
<img width="1892" height="900" alt="image" src="https://github.com/user-attachments/assets/b658b022-3228-41a0-948d-a5e5561362ab" />

## Difference between origin and upstream

origin:
The remote repository you cloned or own.

upstream:
The original repository from which your fork was created.

# Task 4 

git fetch:
Downloads new changes from the remote repository but does not merge them.

git pull:
Downloads the changes and automatically merges them into the current branch.

# Task - 5 
## Difference between clone and fork

Clone:
Creates a local copy of a repository.

Fork:
Creates your own copy of a repository on GitHub.

------------------------------------------------

## When would you clone vs fork?

Clone:
When you have access to the repository and want to work locally.

Fork:
When you want to contribute to someone else's project without modifying the original repository.

------------------------------------------------

## How do you keep your fork in sync?

Add the original repository as the upstream remote.

git remote add upstream <original-repository-url>

Fetch changes.

git fetch upstream

Merge them into your branch.

git merge upstream/main
