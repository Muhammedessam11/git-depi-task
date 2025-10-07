# Git Flow & Stash Practice Task

This project demonstrates a complete practical exercise using **Git Flow** and **Git Stash**, including feature development, conflict resolution, releases, hotfixes, and stash operations.

## 🧭 Task 1: Implementing a Feature Using Git Flow

### Scenario: User Login System

We are developing a **User Login System** for a banking app using Git Flow manually. All merges are done via **Pull Requests**.

---

### 📝 Step 1: Repository Setup

- Clone the repository.
- Initialize Git.
- Create `main` and `development` branches.
- Add file `f1` to both branches.

```bash
git init
git checkout -b main
echo "Initial content" > f1
git add .
git commit -m "Initial commit on main"

git checkout -b development
git add f1
git commit -m "Initial commit on development"

---

### 🌿 Step 2: Create Feature Branch

- Create a feature branch from development for the login functionality.
- Initialize Git.
- Add the line "Implement the login functionality" to f1.
- Commit and push.

```bash
git checkout development
git checkout -b feature/login
echo "Implement the login functionality" >> f1
git add f1
git commit -m "Implement login functionality"
git push origin feature/login

---

### ⚔️ Step 3: Merge Conflict
- Modify f1 in both feature/login and development.
- Attempt to merge feature into development → conflict occurs.
- Resolve manually and commit.

```bash
echo "Development change" >> f1
git commit -am "Update f1 in development"

git merge feature/login
git add f1
git commit


---


### 🔀 Step 4: Merge Feature

- Merge the feature branch into development cleanly.
- Delete the feature branch after merge.

```bash
git checkout development
git merge feature/login --no-ff
git branch -d feature/login
git push origin --delete feature/login


---

### 🚀 Step 5: Release Branch

- Create a release branch from development.

```bash
git checkout development
git checkout -b release/v1.0

---

### ✍️ Step 6: Add Multiple Commits in Feature Branch

- Switch back to feature/login.
- Add 3 commits in f1 (Case 1, Case 2, Case 3).

```bash
git checkout feature/login
echo "Case 1" >> f1
git commit -am "Add Case 1"

echo "Case 2" >> f1
git commit -am "Add Case 2"

echo "Case 3" >> f1
git commit -am "Add Case 3"


---

### ✨ Step 7: Selective Merge & Release
- Switch back to release branch.
- Merge Case 1 and Case 2 only (e.g., using cherry-pick).

```bash
git checkout release/v1.0
git cherry-pick <commit-hash-case1>
git cherry-pick <commit-hash-case2>

Merge the release branch into main.

git checkout main
git merge release/v1.0

Merge the release branch back into development to keep it updated.

git checkout development
git merge release/v1.0
git branch -d release/v1.0
git push origin --delete release/v1.0

---

### 🛠️ Step 8: Hotfix

- Create a hotfix branch from main.
- Fix the issue and commit.
- Merge hotfix into both main and development.

```bash
git checkout main
git checkout -b hotfix/security-fix
echo "Security fix applied" >> f1
git commit -am "Hotfix: Security issue"

git checkout main
git merge hotfix/security-fix

git checkout development
git merge hotfix/security-fix

git branch -d hotfix/security-fix

---

### 🐞 Step 9: Debugging

- Check commit history.
- Revert Case 2 commit from development.

```bash
git log --oneline
git revert <case-2-commit-hash>


---


## 🧭 Task 2: Git Stash

### Scenario: You're working on a new feature but need to switch branches to fix a bug. You haven't committed your changes yet and don't want to lose them.

What git stash Does : git stash temporarily saves your uncommitted changes (both staged and unstaged) and reverts your working directory to a clean state, allowing you to switch branches safely.

### Commands Used:
- git stash
- git stash list
- git stash apply
- git stash pop
- git stash save "message"
- git stash drop stash@{n}
- git stash clear
- git stash apply stash@{n}

---

## ✅ Summary

### This task covered:
- Manual Git Flow branching strategy.
- Working with feature, release, and hotfix branches.
- Conflict resolution and selective cherry-picks.
- Using git stash effectively for temporary changes.

## 🧑‍💻 Author
### Muhammad Essam
