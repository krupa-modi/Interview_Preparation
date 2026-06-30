# Git & GitHub & GitLab Complete Interview Notes 🚀

# 1. What is Git?

Git is a Distributed Version Control System (DVCS).

It helps developers:
- Track code changes
- Collaborate with team members
- Restore old versions
- Manage project history
- Work on features separately

---

# 2. Why Git is Used?

## Without Git Problems:
- Code overwrite ho jata
- Old code recover nahi hota
- Team collaboration difficult hota
- Backup maintain karna hard hota

## With Git Benefits:
- Code history save hoti
- Multiple developers together work kar sakte
- Branching possible hoti
- Easy rollback
- Fast collaboration

---

# 3. What is GitHub?

GitHub is a cloud platform where Git repositories store hote hai.

Use Cases:
- Code hosting
- Team collaboration
- Pull requests
- CI/CD
- Open source projects

Example:
```bash
https://github.com
````

---

# 4. What is GitLab?

GitLab bhi Git hosting platform hai.

Difference:

* GitHub more popular
* GitLab strong DevOps & CI/CD support deta

---

# 5. Difference Between Git, GitHub, GitLab

| Feature         | Git             | GitHub       | GitLab               |
| --------------- | --------------- | ------------ | -------------------- |
| Type            | Tool            | Platform     | Platform             |
| Internet Needed | No              | Yes          | Yes                  |
| Used For        | Version Control | Code Hosting | Code Hosting + CI/CD |
| Local/Cloud     | Local           | Cloud        | Cloud                |

---

# 6. Git Workflow

```text
Working Directory
      ↓
Staging Area
      ↓
Local Repository
      ↓
Remote Repository
```

---

# 7. Important Git Terms

## Repository (Repo)

Project folder managed by Git.

---

## Commit

Snapshot of code changes.

---

## Branch

Separate line of development.

---

## Merge

Combining branches.

---

## Clone

Copying repository from remote.

---

## Push

Uploading code to remote.

---

## Pull

Downloading latest code.

---

## Fork

Copy someone else's repository.

---

## HEAD

Current branch/latest commit pointer.

---

# 8. Git Installation Check

```bash
git --version
```

---

# 9. Configure Git

## Set Username

```bash
git config --global user.name "Krupa"
```

## Set Email

```bash
git config --global user.email "abc@gmail.com"
```

## Check Config

```bash
git config --list
```

---

# 10. Initialize Repository

```bash
git init
```

Purpose:
Creates empty Git repository.

---

# 11. Check Status

```bash
git status
```

Purpose:
Shows modified, staged, untracked files.

---

# 12. Add Files

## Add Single File

```bash
git add index.js
```

## Add All Files

```bash
git add .
```

---

# 13. Commit Changes

```bash
git commit -m "Added login feature"
```

Purpose:
Save changes permanently.

---

# 14. Commit Directly

```bash
git commit -am "message"
```

Note:
Only works for tracked files.

---

# 15. View Commit History

```bash
git log
```

Short version:

```bash
git log --oneline
```

---

# 16. Clone Repository

```bash
git clone repository-url
```

Example:

```bash
git clone https://github.com/user/project.git
```

---

# 17. Remote Repository

## Add Remote

```bash
git remote add origin url
```

## Check Remote

```bash
git remote -v
```

---

# 18. Push Code

## First Push

```bash
git push -u origin main
```

## Normal Push

```bash
git push
```

---

# 19. Pull Latest Code

```bash
git pull
```

---

# 20. Fetch Changes

```bash
git fetch
```

Difference:

* fetch = download only
* pull = download + merge

---

# 21. Branch Commands

## Create Branch

```bash
git branch feature
```

## Switch Branch

```bash
git checkout feature
```

OR

```bash
git switch feature
```

---

## Create + Switch Together

```bash
git checkout -b feature
```

---

## View Branches

```bash
git branch
```

---

## Delete Branch

```bash
git branch -d feature
```

Force delete:

```bash
git branch -D feature
```

---

# 22. Merge Branch

```bash
git merge feature
```

Purpose:
Combine feature branch into current branch.

---

# 23. Merge Conflict

When same line modified by multiple developers.

How to solve:

* Open conflicted file
* Remove conflict markers
* Keep correct code
* Commit again

Conflict markers:

```bash
<<<<<<< HEAD
Your code
=======
Other code
>>>>>>> branch
```

---

# 24. Git Restore

## Restore File

```bash
git restore file.js
```

---

# 25. Remove File

```bash
git rm file.js
```

---

# 26. Rename File

```bash
git mv old.js new.js
```

---

# 27. Reset Commands

## Soft Reset

```bash
git reset --soft HEAD~1
```

Keeps changes staged.

---

## Mixed Reset

```bash
git reset HEAD~1
```

Keeps changes unstaged.

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

Deletes changes completely.

---

# 28. Revert Commit

```bash
git revert commit-id
```

Creates reverse commit safely.

---

# 29. Stash Commands

## Save Temporary Changes

```bash
git stash
```

## View Stash

```bash
git stash list
```

## Apply Stash

```bash
git stash apply
```

## Delete Stash

```bash
git stash drop
```

---

# 30. Difference Between Reset & Revert

| Reset           | Revert        |
| --------------- | ------------- |
| Deletes history | Keeps history |
| Dangerous       | Safe          |
| Used locally    | Used in teams |

---

# 31. Git Ignore

Create:

```bash
.gitignore
```

Example:

```bash
node_modules
.env
dist
```

Purpose:
Ignore unnecessary files.

---

# 32. Git Diff

## Check Changes

```bash
git diff
```

## Staged Changes

```bash
git diff --staged
```

---

# 33. Cherry Pick

```bash
git cherry-pick commit-id
```

Purpose:
Copy specific commit.

---

# 34. Tagging

## Create Tag

```bash
git tag v1.0
```

## Push Tag

```bash
git push origin v1.0
```

---

# 35. Git Rebase

```bash
git rebase main
```

Purpose:
Move branch commits on top of another branch.

---

# 36. Difference: Merge vs Rebase

| Merge                | Rebase          |
| -------------------- | --------------- |
| Keeps history        | Cleaner history |
| Creates merge commit | No merge commit |
| Safer                | Risky sometimes |

---

# 37. Fork vs Clone

| Fork           | Clone       |
| -------------- | ----------- |
| Server copy    | Local copy  |
| GitHub feature | Git command |

---

# 38. Pull Request (PR)

Used to request code merge into main branch.

Process:

* Push code
* Create PR
* Review
* Merge

---

# 39. CI/CD

## CI

Continuous Integration

## CD

Continuous Deployment/Delivery

GitLab famous for built-in CI/CD.

---

# 40. SSH Setup

## Generate SSH Key

```bash
ssh-keygen -t rsa -b 4096
```

## Check SSH

```bash
ssh -T git@github.com
```

---

# 41. Important GitHub Features

* Repository
* Issues
* Pull Requests
* Actions
* Wiki
* Projects
* Discussions

---

# 42. GitHub Actions

Automation tool for:

* Testing
* Build
* Deploy

---

# 43. Common Interview Questions

# Q1. What is Git?

Git is distributed version control system used to track code changes.

---

# Q2. Difference between Git and GitHub?

Git is tool.
GitHub is cloud platform for hosting Git repositories.

---

# Q3. What is branch?

Independent development line.

---

# Q4. What is merge conflict?

When same code lines modified by different developers.

---

# Q5. Difference between pull and fetch?

Fetch downloads only.
Pull downloads + merges.

---

# Q6. What is stash?

Temporary storage for uncommitted changes.

---

# Q7. What is HEAD in Git?

Pointer to current commit.

---

# Q8. What is rebase?

Moves commits to new base.

---

# Q9. What is cherry-pick?

Copies specific commit.

---

# Q10. What is origin?

Default remote repository name.

---

# 44. Real Project Workflow

```text
1. Clone repo
2. Create branch
3. Write code
4. git add .
5. git commit
6. git pull
7. git push
8. Create PR
9. Code review
10. Merge
```

---

# 45. Most Important Commands Revision

```bash
git init
git clone
git status
git add .
git commit -m ""
git push
git pull
git fetch
git branch
git checkout
git merge
git stash
git reset
git revert
git log
git diff
git remote -v
```

---

# 46. Advanced Commands

## Amend Last Commit

```bash
git commit --amend
```

---

## Squash Commits

```bash
git rebase -i HEAD~3
```

---

## Remove Remote

```bash
git remote remove origin
```

---

## Show File History

```bash
git blame file.js
```

---

## Clean Untracked Files

```bash
git clean -f
```

---

# 47. Git Best Practices

* Commit small changes
* Write meaningful commit messages
* Pull before push
* Use feature branches
* Never push secrets
* Use .gitignore properly

---

# 48. Best Commit Message Examples

✅ Good:

```bash
git commit -m "Added login validation"
```

❌ Bad:

```bash
git commit -m "changes"
```

---

# 49. Important Git Interview Topics

Must Prepare:

* Git workflow
* Branching
* Merge conflict
* Rebase
* Stash
* Reset vs Revert
* Pull vs Fetch
* CI/CD basics
* Pull Requests
* GitHub Actions

---

# 50. Final Interview Tips

## Small Companies

Mostly ask:

* Basic commands
* Push/pull
* Branching
* Merge conflict

---

## Medium Companies

Ask:

* Rebase
* Stash
* PR workflow
* CI/CD basics

---

## MNC Companies

Ask:

* Cherry-pick
* Squash
* Advanced branching
* Git internals
* Hooks
* GitHub Actions
* DevOps integration

---

# 51. One-Line Revision

```text
Git = Version Control
GitHub/GitLab = Code Hosting Platforms
Branch = Separate work area
Commit = Save snapshot
Push = Upload
Pull = Download + Merge
Fetch = Download only
Merge = Combine branches
Rebase = Cleaner history
Stash = Temporary save
PR = Request merge
```

---

# 52. Super Important Interview Scenario Questions

# Scenario 1:

You pushed wrong code. What will you do?

Answer:

* Use git revert if shared branch
* Use reset if local only

---

# Scenario 2:

Two developers changed same file. What happens?

Answer:
Merge conflict occurs.

---

# Scenario 3:

Why use feature branches?

Answer:
To isolate development safely.

---

# Scenario 4:

Why .gitignore used?

Answer:
To ignore unnecessary/sensitive files.

---

# Scenario 5:

Difference between local repo and remote repo?

Local:
Your system.

Remote:
GitHub/GitLab server.

---

# 53. GitHub vs GitLab Interview Answer

GitHub:

* Popular
* Open source friendly
* Large community

GitLab:

* Better built-in DevOps
* Strong CI/CD
* Self-hosting support

---

# 54. Important Files

## .gitignore

Ignore files.

## README.md

Project documentation.

## package-lock.json

Dependency lock file.

---

# 55. Most Asked Practical Commands

```bash
git clone
git pull
git checkout -b feature
git add .
git commit -m "msg"
git push origin feature
```

---

# 56. Final Quick Revision Sheet

```text
git init → Start repo
git clone → Copy repo
git add → Stage files
git commit → Save changes
git push → Upload code
git pull → Download latest code
git branch → Branch management
git checkout → Switch branch
git merge → Combine branches
git stash → Temporary save
git reset → Undo commits
git revert → Reverse commit safely
```

# Git Important Terms & Commands (Interview Purpose)

---

## 1. Clean Untracked Files

### What is it?
Remove files that are not tracked by Git.

### Command
```bash
git clean -f
````

### Use Case

When unwanted files are created and you want to delete them.

### Important

* `-f` means force delete.
* Only removes untracked files.

---

## 2. Amend Last Commit

### What is it?

Modify the last commit without creating a new commit.

### Command

```bash
git commit --amend
```

### Use Case

* Fix commit message
* Add missed files in last commit

### Example

```bash
git add file.js
git commit --amend
```

---

## 3. Create PR (Pull Request)

### What is PR?

A request to merge your code into another branch (mostly `main` or `develop`).

### Flow

1. Create branch
2. Push code
3. Open PR on GitHub/GitLab
4. Team reviews code
5. Merge PR

### Commands

```bash
git checkout -b feature-login
git push origin feature-login
```

Then create PR from GitHub UI.

### Interview Point

PR is used for:

* Code review
* Collaboration
* Safe merging

---

## 4. `git restore file.js`

### What is it?

Restore file changes back to last committed state.

### Command

```bash
git restore file.js
```

### Use Case

Undo local changes in a file.

### Example

```bash
git restore app.js
```

---

## 5. `git fetch`

### What is it?

Download latest changes from remote repository without merging.

### Command

```bash
git fetch
```

### Difference

* `git fetch` → only downloads
* `git pull` → download + merge

### Interview Point

Used to safely check latest remote changes before merging.

---

## 6. Remote Repository

### What is it?

Repository stored on server/platform like GitHub.

### Example

* GitHub
* GitLab
* Bitbucket

### Common Command

```bash
git remote -v
```

### Add Remote

```bash
git remote add origin https://github.com/user/repo.git
```

---

## 7. Tracked Files

### What are tracked files?

Files that Git is monitoring.

### Example

After:

```bash
git add file.js
```

Git starts tracking that file.

### Types

* Tracked files
* Untracked files

### Check Status

```bash
git status
```

---

# Quick Interview Difference

| Topic          | Meaning                   |
| -------------- | ------------------------- |
| Tracked File   | Git monitors the file     |
| Untracked File | New file not added to Git |
| git fetch      | Download remote changes   |
| git pull       | Fetch + merge             |
| git restore    | Undo local file changes   |
| PR             | Request to merge code     |
| Amend Commit   | Edit last commit          |


# Advanced Git Interview Questions & Scenarios (3–4 Years Experience)

These are commonly asked in MNC and product-based companies.

---

# 1. Difference Between `git merge` and `git rebase`

| Merge | Rebase |
|---|---|
| Creates merge commit | Cleaner history |
| History remains non-linear | Linear history |
| Safe for teams | Risky if used wrongly |

### Interview Answer
Use `merge` for shared branches and `rebase` for clean commit history.

---

# 2. What happens when you do `git pull`?

### Answer
`git pull` does:
```bash
git fetch + git merge
````

First downloads latest changes then merges into current branch.

---

# 3. Difference Between `git reset` and `git revert`

| git reset                  | git revert             |
| -------------------------- | ---------------------- |
| Removes commits            | Creates reverse commit |
| Dangerous in shared branch | Safe in shared branch  |
| Changes history            | Keeps history          |

### Scenario

If code already pushed → use `revert`.

---

# 4. What is Stash?

### Answer

Temporary storage for uncommitted changes.

### Commands

```bash
git stash
git stash pop
```

### Scenario

Need to switch branch quickly without committing incomplete work.

---

# 5. What is Cherry Pick?

### Answer

Copy specific commit from one branch to another.

### Command

```bash
git cherry-pick commit-id
```

### Scenario

Need only one bug-fix commit from another branch.

---

# 6. Explain Git Workflow in Company

```text
main/master
   ↓
Create feature branch
   ↓
Development
   ↓
Commit changes
   ↓
Push branch
   ↓
Create PR
   ↓
Code Review
   ↓
Merge
   ↓
Deployment
```

---

# 7. What will happen if two developers modify same line?

### Answer

Merge conflict occurs.

Git cannot decide which code to keep.

---

# 8. How do you resolve merge conflicts?

### Steps

1. Open conflicted file
2. Remove conflict markers
3. Keep correct code
4. `git add .`
5. Commit again

---

# 9. What is Detached HEAD State?

### Answer

When HEAD points directly to commit instead of branch.

### Example

```bash
git checkout commit-id
```

### Important

Changes may get lost if branch not created.

---

# 10. What is HEAD in Git?

### Answer

Pointer to current active commit/branch.

---

# 11. Difference Between Fork and Clone

| Fork             | Clone       |
| ---------------- | ----------- |
| Server-side copy | Local copy  |
| GitHub feature   | Git command |

---

# 12. What is Squash Commit?

### Answer

Combine multiple commits into single commit.

### Command

```bash
git rebase -i HEAD~3
```

### Benefit

Cleaner PR history.

---

# 13. Explain `.gitignore`

### Purpose

Ignore unnecessary files.

### Example

```bash
node_modules
.env
dist
```

---

# 14. Scenario: Accidentally committed sensitive data

### Answer

1. Remove file
2. Change credentials immediately
3. Use:

```bash
git reset
```

OR

```bash
git filter-branch
```

---

# 15. Scenario: Wrong commit pushed to main branch

### Best Answer

Use:

```bash
git revert commit-id
```

Never use hard reset on shared branch.

---

# 16. Difference Between `origin` and `upstream`

| Term     | Meaning             |
| -------- | ------------------- |
| origin   | Your repository     |
| upstream | Original repository |

---

# 17. What is Fast Forward Merge?

### Answer

When branch history is linear and Git moves pointer forward without merge commit.

---

# 18. What is Git Hook?

### Answer

Scripts that run automatically before/after Git events.

### Examples

* pre-commit
* pre-push

### Use Cases

* Run tests
* Check linting
* Prevent bad commits

---

# 19. Explain Rebase Conflict

### Answer

During rebase if same code modified, conflict occurs.

### Continue Rebase

```bash
git rebase --continue
```

### Cancel Rebase

```bash
git rebase --abort
```

---

# 20. Difference Between `git fetch` and `git pull`

| Fetch         | Pull                    |
| ------------- | ----------------------- |
| Download only | Download + merge        |
| Safer         | Directly changes branch |

---

# 21. Scenario: Need latest code but don't want merge immediately

### Answer

Use:

```bash
git fetch
```

---

# 22. Scenario: Need to undo local changes completely

### Commands

```bash
git restore .
```

OR

```bash
git reset --hard
```

---

# 23. Scenario: Commit done in wrong branch

### Solution

1. Create new branch
2. Cherry-pick commit
3. Remove commit from wrong branch

---

# 24. Scenario: PR has too many commits

### Answer

Use squash/rebase before merge.

---

# 25. What is CI/CD in GitHub/GitLab?

### CI

Automatically build/test code.

### CD

Automatically deploy code.

### Tools

* GitHub Actions
* Jenkins
* GitLab CI/CD

---

# 26. Scenario-Based Interview Questions

## Q1.

You and teammate changed same file. What happens?

### Answer

Merge conflict.

---

## Q2.

You want temporary backup without commit.

### Answer

Use stash.

---

## Q3.

You pushed wrong code to production branch.

### Answer

Use revert instead of reset.

---

## Q4.

Need one commit from another branch only.

### Answer

Use cherry-pick.

---

## Q5.

How do you keep commit history clean?

### Answer

Use rebase/squash.

---

# 27. Important Commands for Experienced Developers

```bash
git stash
git cherry-pick
git rebase
git revert
git reset
git blame
git clean
git reflog
git squash
git fetch
git restore
```

---

# 28. What is `git reflog`?

### Answer

Shows history of HEAD movements.

### Command

```bash
git reflog
```

### Use Case

Recover deleted/lost commits.

---

# 29. What is `git blame`?

### Answer

Shows who changed each line in file.

### Command

```bash
git blame app.js
```

---

# 30. Real Company Best Practices

* Always pull before push
* Use feature branches
* Small meaningful commits
* Never push secrets
* Write proper PR description
* Resolve conflicts carefully
* Use rebase for clean history

---

# Most Important Topics for 3–4 Years Experience

✅ Rebase
✅ Merge Conflict
✅ PR Workflow
✅ Stash
✅ Cherry-pick
✅ Reset vs Revert
✅ CI/CD Basics
✅ Git Hooks
✅ Squash Commits
✅ Reflog
✅ Feature Branch Workflow


# What is Code Review?

Code review means checking another developer’s code before merging into main branch.

Purpose:
- Improve code quality
- Find bugs
- Maintain clean code
- Share knowledge

---

# Best Practices

## 1. Keep PR Small

Small pull requests are easier to review and understand.

---

## 2. Check Code Readability

Code should be:
- Clean
- Simple
- Easy to understand

Use meaningful variable and function names.

---

## 3. Follow Coding Standards

Check:
- Naming conventions
- Folder structure
- Formatting
- Best practices

---

## 4. Focus on Logic

Review:
- Business logic
- Edge cases
- Error handling
- Performance issues

---

## 5. Avoid Hardcoded Values

Use:
- Constants
- Environment variables

---

# Bad Example

```js id="pr0f2y"
const api = "test123";
````

---

# Good Example

```js id="m8x7qw"
const API_URL = process.env.API_URL;
```

---

## 6. Check Reusability

Avoid duplicate code.

Create reusable functions/components.

---

## 7. Write Constructive Feedback

Good review comments should:

* Be respectful
* Explain issue clearly
* Suggest improvements

---

# Bad Comment

```text id="v3n6ks"
This is wrong.
```

---

# Good Comment

```text id="r1m9qt"
Can we move this logic into a reusable helper function for better maintainability?
```

---

## 8. Check Performance

Look for:

* Unnecessary re-renders
* Large loops
* Unoptimized API calls

---

## 9. Ensure Proper Testing

Verify:

* Unit tests added
* Existing tests passing

---

## 10. Security Checks

Check for:

* Sensitive data exposure
* Input validation
* Authentication issues

---

# Important Interview Points

| Best Practice         | Purpose            |
| --------------------- | ------------------ |
| Small PRs             | Easy review        |
| Clean code            | Better readability |
| Reusability           | Less duplication   |
| Proper testing        | Fewer bugs         |
| Constructive feedback | Better teamwork    |

---

# Short Interview Answer

```text id="x7n4pq"
Code review improves code quality and helps find bugs before deployment. 
Best practices include keeping PRs small, checking readability, performance, testing, security and giving constructive feedback.
```


# Git Stage vs Unstaged

## 1. Unstaged Changes

जब आप file में changes करते हो लेकिन अभी तक Git को नहीं बताया कि ये changes save करने हैं, तब वो **unstaged** होते हैं।

### Example

```bash
git status
```

Output:

```bash
modified: app.js
```

मतलब file change हुई है लेकिन अभी commit के लिए ready नहीं है।

---

## 2. Staged Changes

जब आप `git add` करते हो, तब changes **staged** हो जाते हैं।

### Example

```bash
git add app.js
```

अब Git बोलता है:
“ठीक है, ये changes next commit में डालने हैं।”

---

## Simple Flow

```bash
File Change
    ↓
Unstaged
    ↓ git add
Staged
    ↓ git commit
Saved in Git
```

---

## Important Commands

### Unstaged देखने के लिए

```bash
git status
```

### Stage करने के लिए

```bash
git add filename
```

### Stage हटाने के लिए

```bash
git restore --staged filename
```

---

## Real Life Example

मान लो आपने `index.js` में code लिखा।

* अभी सिर्फ save किया → **Unstaged**
* `git add index.js` किया → **Staged**
* `git commit` किया → permanently save in Git history


# Git Reset vs Revert vs Merge vs Rebase

## 1. Git Reset

### Purpose

Commit या staged changes को पीछे ले जाने के लिए use होता है।

### Command

```bash id="5axr5m"
git reset HEAD~1
```

### What Happens?

* Commit history change हो सकती है
* Changes remove या unstage हो सकते हैं

### Types

| Type      | Meaning                            |
| --------- | ---------------------------------- |
| `--soft`  | Commit हटेगा but code staged रहेगा |
| `--mixed` | Commit हटेगा + unstaged हो जाएगा   |
| `--hard`  | Commit और code दोनों delete        |

### Example

```bash id="c5g7z5"
git reset --hard HEAD~1
```

Last commit और code दोनों हट जाएंगे।

### Use Case

* Local mistake fix करना
* Wrong commit हटाना

### Important

⚠️ Shared branch पर `reset` dangerous हो सकता है।

---

# 2. Git Revert

### Purpose

Old commit को undo करना without history delete किए।

### Command

```bash id="0f3v4z"
git revert commit_id
```

### What Happens?

* Old commit delete नहीं होता
* नया reverse commit बनता है

### Example

```bash id="d7x1dn"
git revert a123bc
```

अगर किसी commit ने:

```js id="m14tlj"
console.log("Hello")
```

add किया था, revert नया commit बनाकर उसे remove करेगा।

### Use Case

* Production bug rollback
* Team projects

### Important

✅ Safe for shared branches

---

# 3. Git Merge

### Purpose

2 branches को combine करने के लिए।

### Command

```bash id="0j3slq"
git merge feature-branch
```

### What Happens?

* Branch histories combine होती हैं
* Merge commit बन सकता है

### Example

```bash id="mjlwmv"
main
  A---B

feature
      C---D
```

After merge:

```bash id="kjskup"
main
  A---B-------M
       \     /
        C---D
```

### Use Case

* Feature complete होने के बाद main में add करना

### Important

✅ History safe रहती है
❌ History थोड़ी messy हो सकती है

---

# 4. Git Rebase

### Purpose

Branch history को clean और linear बनाना।

### Command

```bash id="8rnhvq"
git rebase main
```

### What Happens?

Feature branch commits को main के latest commit के ऊपर move करता है।

### Example

Before:

```bash id="jlwm6w"
main
A---B

feature
    C---D
```

After rebase:

```bash id="i6f7h6"
main
A---B

feature
        C'---D'
```

(C and D new commits बन जाते हैं)

### Use Case

* Clean history
* Pull request clean रखना

### Important

✅ Linear history
❌ Shared branch पर risky हो सकता है

---

# Main Difference Table

| Feature            | Reset        | Revert      | Merge            | Rebase        |
| ------------------ | ------------ | ----------- | ---------------- | ------------- |
| Purpose            | Undo commits | Undo safely | Combine branches | Clean history |
| History Changes    | Yes          | No          | No               | Yes           |
| Safe for Team      | ❌            | ✅           | ✅                | ⚠️            |
| New Commit Created | ❌            | ✅           | ✅                | ❌             |
| Deletes Commit     | Yes          | No          | No               | Rewrites      |

---

# Easy Memory Trick

| Command | Easy Meaning             |
| ------- | ------------------------ |
| Reset   | “Delete/Move Back”       |
| Revert  | “Undo Safely”            |
| Merge   | “Join Branches”          |
| Rebase  | “Clean & Linear History” |

---

# Interview One-Line Answers

### Reset

Moves HEAD backward and can remove commits/history.

### Revert

Creates a new commit to undo old changes safely.

### Merge

Combines two branches while preserving history.

### Rebase

Moves branch commits on top of another branch for clean history.


# SSH in Git

## Full Form

**SSH = Secure Shell**

---

## Why SSH is Used in Git

SSH Git में secure connection बनाने के लिए use होता है।

जब हम GitHub/GitLab/Bitbucket पर code push या pull करते हैं, तब SSH encrypted connection provide करता है।

---

## Main Purpose

* Secure authentication
* Password बार-बार डालने की जरूरत नहीं
* Safe data transfer
* Developer machine और Git server के बीच trusted connection

---

## How it Works

SSH में 2 keys होती हैं:

1. **Public Key** → GitHub पर add करते हैं
2. **Private Key** → आपकी system में रहती है

जब connection बनता है, GitHub verify करता है कि आप authorized user हो।

---

## Interview Line

> “SSH is used in Git to create a secure authenticated connection between local machine and remote repository without entering username and password every time.”

---

## SSH vs HTTPS

| SSH                    | HTTPS                          |
| ---------------------- | ------------------------------ |
| More secure            | Simple setup                   |
| No password every time | Username/password/token needed |
| Uses SSH keys          | Uses credentials               |

---

## Common SSH Command

### Generate SSH Key

```bash id="b9z42l"
ssh-keygen -t ed25519 -C "your_email@gmail.com"
```

### Test Connection

```bash id="ew4qz9"
ssh -T git@github.com
```

---

## Example SSH URL

```bash id="n7gx54"
git@github.com:user/repo.git
```

---

## Short Interview Answer

> SSH stands for Secure Shell.
> It is used in Git for secure communication and authentication between local system and remote repository using SSH keys.
