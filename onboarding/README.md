# Dataria Onboarding Checklist Process

Welcome to Dataria! This directory contains your onboarding checklist process.

## 🎯 Purpose

The onboarding checklist serves multiple purposes:
1. **Track your progress** through the setup process
2. **Document your experience** to help improve onboarding
3. **Learn Git workflow** by creating your first Pull Request
4. **Share knowledge** with future new joiners

## 📝 How to Use the Checklist

### Step 1: Create Your Checklist

Copy the template and create your personal checklist:

```bash
# Navigate to the docs directory
cd docs/onboarding

# Copy the template with your name (use lowercase and hyphens)
cp TEMPLATE.md checklists/firstname-lastname.md

# Example:
# cp TEMPLATE.md checklists/john-smith.md
```

### Step 2: Fill Out Your Checklist

As you go through the onboarding process:

1. Open your checklist file in your editor
2. Check off items as you complete them: `- [x]`
3. Add notes about your experience, issues, or solutions
4. Fill in versions, dates, and other details
5. Save your changes regularly

Example of a completed item:
```markdown
- [x] **Dataria Slack** - Joined workspace and introduced myself in #general
  - Slack workspace URL: dataria.slack.com
  - Notes: Found the #introductions channel very helpful!
```

### Step 3: Commit Your Progress

Commit your changes regularly (at least daily):

```bash
# Create your feature branch
git branch onboarding/firstname-lastname-onboarding

# Checkout to your feature branch
git checkout onboarding/firstname-lastname-onboarding

# Stage your changes
git add onboarding/checklists/firstname-lastname.md

# Commit with a descriptive message
git commit -m "Update onboarding checklist - completed platform setup"

# Push to your branch
git push origin onboarding/firstname-lastname-onboarding
```

### Step 4: Create a Pull Request

When you've completed most of your onboarding:

#### Using GitHub CLI (Recommended)
```bash
# Create PR using GitHub CLI
gh pr create \
  --title "Onboarding Checklist - Firstname Lastname" \
  --body "My completed onboarding checklist. Feedback and suggestions included for improving the process." \
  --label "onboarding"
```

#### Using GitHub Web Interface
1. Push your branch: `git push origin onboarding/firstname-lastname`
2. Go to https://github.com/datariaengineers/docs
3. Click "Pull requests" > "New pull request"
4. Select your branch
5. Add title: "Onboarding Checklist - Firstname Lastname"
6. Add description about your experience
7. Add label: "onboarding"
8. Click "Create pull request"

### Step 5: Request Review

Ask your manager and buddy to review your PR:

```bash
# Using GitHub CLI
gh pr review request @manager-username @buddy-username

# Or tag them in a PR comment
# @manager-username @buddy-username Please review my onboarding checklist!
```

## 📊 PR Review Process

### What Reviewers Look For

Your manager and team will review:
- ✅ Completeness of setup
- 📝 Feedback and suggestions for improvement
- 🐛 Any blockers or issues encountered
- 💡 Ideas for making onboarding better

### After Review

- Address any feedback or questions
- Make updates if needed
- Once approved, your PR will be merged
- Your checklist becomes part of our onboarding knowledge base!

## 🎓 Learning Objectives

By completing this process, you'll learn:

### Git & GitHub Workflow
- Creating branches
- Making commits with good messages
- Pushing changes to remote
- Creating Pull Requests
- Responding to code review
- Merging changes

### Collaboration
- Using GitHub for team collaboration
- Documenting your work
- Giving and receiving feedback
- Contributing to team knowledge

### Communication
- Writing clear PR descriptions
- Using GitHub mentions and notifications
- Asking for help when needed

## 📁 Directory Structure

```
onboarding/
├── README.md           # This file - instructions
├── TEMPLATE.md         # Checklist template
└── checklists/         # Completed checklists
    ├── john-smith.md
    ├── jane-doe.md
    └── [your-name].md
```

## 💡 Tips for Success

### Good Commit Messages
```bash
# Good ✅
git commit -m "Complete Python and Terraform setup sections"
git commit -m "Add notes about pyenv installation issue on macOS"
git commit -m "Update feedback section with suggestions"

# Not so good ❌
git commit -m "update"
git commit -m "changes"
git commit -m "wip"
```

### Detailed Notes Are Valuable
When you encounter issues, document:
- **What went wrong**: Specific error messages
- **How you fixed it**: Steps you took to resolve it
- **Time spent**: Helps us improve estimates
- **Resources used**: Links, docs, or people who helped

Example:
```markdown
- [x] Installed pyenv
  - Version: 2.3.24
  - Notes: Had to install Xcode Command Line Tools first.
    Ran into "BUILD FAILED" error. Fixed by running:
    brew install openssl readline sqlite3 xz zlib
    Then pyenv install worked fine. Took about 30 minutes total.
```

### Ask Questions Early
If you're stuck for more than 15-20 minutes:
1. Check the troubleshooting section in docs
2. Search Slack for similar issues
3. Ask in #tech or #general channel
4. Reach out to your buddy or manager

Don't spend hours debugging alone! We're here to help.

## 🆘 Getting Help

- **Git/GitHub Issues**: Ask your buddy or post in #tech
- **Setup Problems**: Check troubleshooting sections in docs
- **Tool Questions**: #tech channel on Slack
- **Process Questions**: Ask your manager

## 🎯 Example Timeline

Here's a typical timeline for completing the onboarding checklist:

| Day | Activities | Checklist Sections |
|-----|------------|-------------------|
| **Day 1** | Access setup, platform installation | Essential Access, Platform Setup |
| **Day 2** | Python & development tools | Python Setup, Terraform Setup |
| **Day 3** | CLI tools, IDE setup | CLI Tools, IDE Setup |
| **Day 4** | Configuration, Git setup, first clone | Configuration, Git Setup |
| **Day 5** | Create onboarding PR, first task | First Repository, PR Creation |
| **Week 2+** | Team integration, first contributions | Team Integration, First Contributions |

## 📚 Reference

### Useful Git Commands

```bash
# Check status
git status

# View your changes
git diff

# View commit history
git log --oneline

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo changes to a file
git checkout -- filename.md

# Update your branch with latest main
git fetch origin
git rebase origin/main
```

### Useful GitHub CLI Commands

```bash
# View your PRs
gh pr list --author @me

# View PR status
gh pr status

# Check PR in browser
gh pr view --web

# Add reviewers
gh pr edit --add-reviewer username
```

## 🎉 After Your PR Is Merged

Congratulations! You've:
- ✅ Completed your development environment setup
- ✅ Made your first contribution to Dataria
- ✅ Learned the Git/GitHub workflow
- ✅ Helped improve our onboarding process

Your checklist will help future new joiners learn from your experience!

---

**Questions?** Ask in #general or reach out to your manager!