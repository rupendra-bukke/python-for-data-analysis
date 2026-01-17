# Git Workflow Guide

## Overview
This guide explains how to push your local files to GitHub using Git.

---

## The Basic Git Workflow

The flow to get your changes from your computer to GitHub:

```
Untracked Files → git add → Staged Files → git commit → Committed → git push → On GitHub
```

---

## Step-by-Step Breakdown

### 1. Check Git Status
```bash
git status
```
**What it does:** Shows you which files have changed or are untracked (new files not yet added to git)

**Output example:**
```
Untracked files:
  - SCRIPT_EXPLANATION.md
  - transform_vehicle_data.py
  - data/vehicle_signal_transformed.csv
```

---

### 2. Configure Git Identity (First Time Only)
```bash
git config --global user.email "your-email@example.com"
git config --global user.name "Your Name"
```

**What it does:** Tells Git who you are. This sets your identity globally on your computer for all commits.

**Example:**
```bash
git config --global user.email "rupendra-bukke@github.com"
git config --global user.name "Rupendra Bukke"
```

---

### 3. Add Files to Staging Area
```bash
git add .
```

**What it does:** Stages all untracked files (the `.` means "everything in current directory"). 

**Think of it as:** Preparing your files for a snapshot.

**Other options:**
- `git add filename.txt` - Add a specific file
- `git add .` - Add all files
- `git add *.py` - Add all Python files

---

### 4. Commit Your Changes
```bash
git commit -m "Your descriptive message here"
```

**What it does:** Creates a snapshot (checkpoint) of your staged files with a description.

**Example:**
```bash
git commit -m "Add vehicle data transformation script and documentation"
```

**Good commit message tips:**
- Be descriptive: "Add feature" ✅
- Be specific: "Fix login bug" ✅
- Avoid vague messages: "stuff" ❌

---

### 5. Push to GitHub
```bash
git push
```

**What it does:** Uploads your commit from your local computer to the remote repository (GitHub).

**After pushing:**
- Your code is backed up online
- Visible in your GitHub repository
- Colleagues can access your changes

---

## Complete Example: Start to Finish

```bash
# 1. Check what changed
git status

# 2. Configure identity (first time only)
git config --global user.email "your-email@example.com"
git config --global user.name "Your Name"

# 3. Add all files
git add .

# 4. Commit with a message
git commit -m "Add vehicle data transformation script and documentation"

# 5. Push to GitHub
git push
```

---

## Key Concepts

| Term | Meaning |
|------|---------|
| **Untracked** | New files Git doesn't know about yet |
| **Staged** | Files ready to be committed |
| **Committed** | Changes saved locally with a message |
| **Pushed** | Changes uploaded to GitHub |
| **Repository** | Your project folder tracked by Git |
| **Main branch** | The primary version of your code |

---

## Common Commands Reference

```bash
# View commit history
git log

# See what changed in your files
git diff

# Create a new branch
git branch branch-name

# Switch branches
git checkout branch-name

# View all branches
git branch -a

# Undo last commit (keep changes)
git reset --soft HEAD~1

# View remote URL
git remote -v
```

---

## Troubleshooting

### "Author identity unknown" error
**Solution:** Run git config commands first (Step 2)

### "Permission denied" error
**Solution:** Verify you have access to the repository on GitHub

### "fatal: Not a git repository" error
**Solution:** Make sure you're in the correct project folder with `.git` directory

---

## Tips for Good Git Practices

✅ **DO:**
- Commit frequently (small, logical changes)
- Write clear, descriptive commit messages
- Pull before pushing to avoid conflicts
- Create branches for new features

❌ **DON'T:**
- Commit everything at once
- Write vague messages like "fixed stuff"
- Push directly to main in team projects
- Commit sensitive information (passwords, API keys)

---

## Next Steps

Once you master this basic workflow, explore:
- **Branching**: Work on features without affecting main code
- **Pull Requests**: Review code before merging to main
- **Merge Conflicts**: Handle when multiple people edit same file
- **.gitignore**: Specify files Git should ignore

---

Happy coding! 🚀
