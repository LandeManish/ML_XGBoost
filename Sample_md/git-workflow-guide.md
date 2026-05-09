# Git Workflow Guide for Beginners

> A practical guide to using Git effectively on a team project.

---

## Prerequisites

- Git installed: `git --version`
- A GitHub / GitLab account
- A project repository cloned locally

---

## Core Concepts

| Term         | What it means                                      |
|--------------|----------------------------------------------------|
| **Repository** | The project folder tracked by Git               |
| **Branch**   | An isolated line of development                    |
| **Commit**   | A saved snapshot of your changes                   |
| **Push**     | Upload local commits to the remote server          |
| **Pull**     | Download and merge remote changes locally          |
| **PR / MR**  | Pull / Merge Request — propose changes for review  |

---

## Step-by-Step Workflow

### 1. Start Fresh — Sync with Main

Always start from an up-to-date `main` branch:

```bash
git checkout main
git pull origin main
```

### 2. Create a Feature Branch

Name branches descriptively:

```bash
git checkout -b feature/user-login
# or for a bug fix:
git checkout -b fix/payment-crash
```

### 3. Make Changes and Stage Them

```bash
# Check what changed
git status

# Stage specific files
git add src/auth/login.py

# Or stage everything
git add .
```

### 4. Commit with a Clear Message

Follow the pattern: `type: short description`

```bash
git commit -m "feat: add JWT-based user login endpoint"
```

**Common types:** `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

### 5. Push Your Branch

```bash
git push origin feature/user-login
```

### 6. Open a Pull Request

- Go to GitHub/GitLab and open a PR from your branch → `main`.
- Add a clear description, link any related issues, and request a reviewer.

### 7. Address Review Comments

Make changes locally, commit, and push — the PR updates automatically.

### 8. Merge and Clean Up

After approval:

```bash
git checkout main
git pull origin main
git branch -d feature/user-login  # delete local branch
```

---

## Useful Commands Cheat Sheet

```bash
git log --oneline          # compact commit history
git diff                   # see unstaged changes
git stash                  # temporarily shelve changes
git stash pop              # restore stashed changes
git reset --soft HEAD~1    # undo last commit, keep changes staged
git blame filename.py      # see who changed each line
```

---

## Common Mistakes to Avoid

- ❌ Committing directly to `main`
- ❌ Giant commits with unrelated changes — keep commits small and focused
- ❌ Vague messages like `"fix stuff"` or `"changes"`
- ❌ Pushing sensitive data (API keys, passwords) — use `.gitignore` and environment variables

---

## Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Flow Guide](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Conventional Commits Spec](https://www.conventionalcommits.org/)

---
_Last updated: 2026-05-09_
