# Git Reset $ Revert

## Task - 1
<img width="1920" height="661" alt="image" src="https://github.com/user-attachments/assets/b10a006d-fabc-4a24-8fca-21b2a4f80d49" />

git reset --soft HEAD~1 (remove last commit from history (c))
<img width="1920" height="993" alt="image" src="https://github.com/user-attachments/assets/28f534db-8615-40d3-a714-245d056f436e" />
<img width="1920" height="977" alt="image" src="https://github.com/user-attachments/assets/f7435d89-3b1d-456f-a257-a3fcb8e4d564" />

| Option              | Commit Removed | Staging Area         | Working Directory |
| ------------------- | -------------- | -------------------- | ----------------- |
| `--soft`            | Yes            | Keeps changes staged | Keeps changes     |
| `--mixed` (default) | Yes            | Unstages changes     | Keeps changes     |
| `--hard`            | Yes            | Clears staging       | Deletes changes   |

## Task 2: Git Revert — Hands-On

## Objective

Practice using `git revert` to undo a specific commit while preserving Git history.

---

## Step 1: Create Commit X

```bash
echo "Commit X" > file.txt
git add file.txt
git commit -m "Commit X"
```

**file.txt**

```text
Commit X
```

---

## Step 2: Create Commit Y

```bash
echo "Commit Y" >> file.txt
git add file.txt
git commit -m "Commit Y"
```

**file.txt**

```text
Commit X
Commit Y
```

---

## Step 3: Create Commit Z

```bash
echo "Commit Z" >> file.txt
git add file.txt
git commit -m "Commit Z"
```

**file.txt**

```text
Commit X
Commit Y
Commit Z
```

---

## Step 4: View Commit History

```bash
git log --oneline
```

Example:

```text
29de2f1 Commit Z
ceb4e75 Commit Y
ba8c41b Commit X
```

---

## Step 5: Revert Commit Y

```bash
git revert <commit-hash-of-Y>
```

Example:

```bash
git revert ceb4e75
```

---

## What Happened?

Git attempted to undo **Commit Y**, but **Commit Z** had already modified the same file.

Since both commits changed `file.txt`, Git could not safely determine how to remove only **Commit Y** without affecting **Commit Z**.

As a result, Git reported a merge conflict.

Example:

```text
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
error: could not revert ceb4e75... Commit Y
```

---

## Step 6: Resolve the Conflict

Git added conflict markers to `file.txt`:

```text
Commit X
<<<<<<< HEAD
Commit Y
Commit Z
=======
>>>>>>> parent of ceb4e75 (Commit Y)
```

Since the goal was to remove **Commit Y** but keep **Commit Z**, the file was edited to:

```text
Commit X
Commit Z
```

---

## Step 7: Mark the Conflict as Resolved

```bash
git add file.txt
```

---

## Step 8: Complete the Revert

```bash
git revert --continue
```

Git created a new commit:

```text
Revert "Commit Y"
```

---

## Verify

```bash
git log --oneline
```

Example:

```text
<new-hash> Revert "Commit Y"
29de2f1 Commit Z
ceb4e75 Commit Y
ba8c41b Commit X
```

Check the file:

```bash
cat file.txt
```

Output:

```text
Commit X
Commit Z
```

---

# Observation

* `git revert` does **not** remove the original commit.
* It creates a **new commit** that reverses the changes made by the selected commit.
* If later commits modify the same lines, Git may produce a merge conflict that must be resolved manually.
* `git revert` is safe for shared branches because it preserves project history.

## Task - 3

| Feature                              | `git reset`                                                                                                    | `git revert`                                                                                                                 |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **What it does**                     | Moves `HEAD` to a previous commit, undoing commits by changing branch history.                                 | Creates a new commit that reverses the changes introduced by a previous commit.                                              |
| **Removes commit from history?**     | **Yes.** The commits after the reset point are removed from the current branch history.                        | **No.** The original commit remains in history, and a new "revert" commit is added.                                          |
| **Safe for shared/pushed branches?** | **No.** It rewrites history and may require a force push, which can disrupt others' work.                      | **Yes.** It preserves history and does not require rewriting or force pushing.                                               |
| **When to use**                      | For undoing **local, unpushed commits**, cleaning up commit history, or fixing recent mistakes before sharing. | For undoing **pushed or shared commits** while keeping the project history intact, especially in collaborative repositories. |


## Task - 4
# Task 4: Branching Strategies

### 1. GitFlow

#### How it works

GitFlow uses multiple long-lived branches:

* **main** – Production-ready code
* **develop** – Integration branch for ongoing development
* **feature/** – New features
* **release/** – Preparing a release
* **hotfix/** – Urgent fixes for production

It is designed for projects with planned release cycles. ([atlassian.com][1])

### Diagram

```text
                 feature/login
                /
main ───────── develop ───────── release/v1.0 ───────► main
                 \
                  feature/payment

main ───────── hotfix/login ─────────────────────────► main
```

#### Used for

* Enterprise applications
* Large teams
* Products with scheduled releases

#### Pros

* Clear separation of development and production
* Supports release planning
* Easy hotfix management
* Well-organized workflow

#### Cons

* Many branches to manage
* More complex
* Slower for continuous deployment

---

## 2. GitHub Flow

#### How it works

Developers create a short-lived feature branch from **main**, make changes, open a Pull Request, get it reviewed, and merge it back into **main**. The **main** branch is always deployable. ([Microsoft Learn][2])

#### Diagram

```text
main
 │
 ├── feature-login ──┐
 │                   │
 ├── feature-cart ───┼──► Pull Request ─► Merge ► main
 │                   │
 └── feature-api ────┘
```

#### Used for

* Startups
* Web applications
* SaaS products
* Continuous Integration/Continuous Deployment (CI/CD)

#### Pros

* Simple and easy to understand
* Fast development
* Frequent deployments
* Minimal branching

#### Cons

* Not ideal for maintaining multiple release versions
* Requires good automated testing

---

## 3. Trunk-Based Development

#### How it works

Developers commit directly to **main (trunk)** or use very short-lived branches that are merged back quickly (usually within a day). Continuous integration and automated testing are essential. ([atlassian.com][1])

#### Diagram

```text
main
 │
 ├── feature A ─► Merge
 │
 ├── feature B ─► Merge
 │
 ├── bug fix ──► Merge
 │
 └── feature C ─► Merge
```

#### Used for

* CI/CD environments
* Cloud-native projects
* Teams deploying multiple times a day

#### Pros

* Fast integration
* Fewer merge conflicts
* Supports continuous delivery
* Encourages small, frequent commits

#### Cons

* Requires strong automated testing
* Bugs can reach the main branch if testing is weak
* Needs disciplined developers

---

## Answers

#### 1. Which strategy would you use for a startup shipping fast?

**GitHub Flow**

**Reason:**

* Simple workflow
* Fast feature delivery
* Easy collaboration
* Ideal for continuous deployment

---

#### 2. Which strategy would you use for a large team with scheduled releases?

**GitFlow**

**Reason:**

* Separate development and production branches
* Dedicated release branches
* Supports hotfixes
* Better suited for planned release cycles

---

#### 3. Which one does your favorite open-source project use?

A good example is Kubernetes.

**Workflow used:** **GitHub Flow–style workflow**

Typical workflow:

1. Create a feature branch from `main`.
2. Make changes and commit.
3. Open a Pull Request.
4. Code review and automated CI tests.
5. Merge into `main` after approval.

