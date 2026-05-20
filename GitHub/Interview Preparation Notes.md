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


