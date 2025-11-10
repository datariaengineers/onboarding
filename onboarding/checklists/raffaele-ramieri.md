# Onboarding Checklist - [Raffaele Ramieri]

**Date Started**: [2026-11-06]
**Team**: [Dataria]
**Manager**: [Azzurra Roberto]
**Operating System**: [x] macOS [ ] Windows

## Instructions

1. Copy this template to `onboarding/checklists/your-name.md`
2. Check off items as you complete them
3. Add notes about any issues or solutions you found
4. Create a Pull Request when done to help improve the onboarding process

---

## Week 1: Essential Access & Setup

### Day 1 - Account Access
- [x] **Dataria Slack** - Joined workspace and introduced myself in #general
  - Slack workspace URL: datariaworkspace.slack.com

- [x] **Linear** - Account created and added to team
  - Team(s): Dataria

- [ ] **AWS Console** - Access granted and verified login
  - Account ID: _____________
  - Region(s): _____________
  - Notes: _____________

- [x] **GitHub** - Added to datariaengineers organization
  - GitHub username: RaffaeleDataria
  - Repositories I have access to: tutte

- [x] **Company Email** - Set up and configured
  - Email address: raffaele@dataria.it

### Day 1-2 - Platform Setup

**I chose**: [x] macOS [ ] Windows

#### Package Manager
- [x] Installed package manager (Homebrew/Scoop)
  - Version: 4.6.20

#### Terminal
- [x] Installed terminal (iTerm2/Windows Terminal)
  - Configuration applied: [ ] Yes [ ] No
  - Custom theme/font: Solarized Dark
  - Notes: 
	1)non ho trovato il tema Tomorrow Night
	2)non ho trovato nessuno dei font raccomandati
	3)l'app si chiama solo iterm
	4)una sezione per consigli su Mac sarebbe
	utile, da windowista non trovo scontato le impostazioni delle
	app si gestiscano da quella che sembra solo
	gui del desktop 
	(ho usato command+, sul momento)

#### Optional Enhancements
- [ ] Oh My Zsh / PowerShell Profile configured
  - Notes: _____________

### Day 2-3 - Development Environment

#### Python Setup
- [x] Installed pyenv
  - Version: 2.6.12

- [x] Installed Python
  - Python version: 3.12.0

- [x] Installed uv
  - Version: 0.9.7
 
- [x] Created test virtual environment
  - Command used: uv venv .venv
  - Worked successfully: [x] Yes [ ] No

#### Terraform Setup
- [x] Installed tfenv
  - Version: 3.0.0

- [x] Installed Terraform
  - Terraform version: 1.13.5

- [x] Installed TFLint
  - Version: 0.59.1

#### CLI Tools
- [x] Installed AWS CLI
  - Version: 2.31.30
  - Configured with credentials: [ ] Yes [x] No
  - Default region: _____________
  - Notes: _____________

- [x] Installed GitHub CLI (gh)
  - Version: 2.83.0
  - Authenticated successfully: [x] Yes [ ] No
  - Notes: _____________

### Day 3-4 - IDE & Editor

**I chose**: [ ] VS Code [x] PyCharm Community [ ] Both

#### PyCharm 
- [x] Installed PyCharm Community
  - Version: 2025.2.4, NB:ora esiste solo una versione

- [x] Configured Python interpreter
  - Interpreter path: _____________ non ho capito

- [x] Installed Terraform plugin

- [x] Installed AWS Toolkit
  - Notes: non so cosa voglia dire install for 	
	   AWS resource management, l'ho solo installato

#### Claude Code
- [x] Installed Claude Code
  - Version: 2.0.36

- [x] Authenticated with Anthropic
  - Status: [x] Success [ ] Pending

- [x] Tested basic commands

### Day 4-5 - Configuration & Git Setup

#### Git Configuration
- [x] Configured Git user name and email
  - Name: RaffaeleDataria
  - Email: raffaele@dataria.it

- [x] Set up Git aliases

- [x] Generated SSH key for GitHub
  - Key type: [x] ed25519 [ ] RSA
  - Added to GitHub: [x] Yes [ ] No

- [x] Tested GitHub SSH connection
  - Result: Hi RaffaeleDataria! You've successfully authenticated, but GitHub does not provide shell access.

#### Shell Configuration
- [ ] Created/updated shell profile
  - Profile location: _____________
  - Added custom aliases: [ ] Yes [ ] No

- [ ] Added environment variables
  - Notes: _____________

#### Project Configuration
- [x] Created .gitignore template
- [x] Created .editorconfig
- [ ] Set up pre-commit hooks (if applicable)

### Day 5 - First Repository

- [x] Cloned first Dataria repository
  - Repository name: scraper
  - Clone method: [x] SSH [ ] HTTPS
  - Notes: il desktop e legato al cloud 

- [x] Installed project dependencies
  - Method used (uv/pip): uv sync
  - Issues: _____________

- [ ] Ran project locally
  - Success: [ ] Yes [ ] No
  - Notes: _____________

- [x] Created this onboarding checklist PR
  - PR number: #_____________
  - Date submitted: _____________

---

## Week 2-4: Team Integration

### Meetings & Introductions
- [x] Attended daily standup
  - Date: 7/11/2025
  - Notes: _____________

- [x] One-on-one with manager
  - Date: 6/11/2025
  - Topics discussed: _____________

- [x] Met with buddy/mentor
  - Buddy name: Azzurra
  - Notes: _____________

- [x] Attended team meeting
  - Date: 06/11/2025
  - Notes: _____________

### Learning & Documentation
- [ ] Read team documentation
  - Key documents reviewed: _____________

- [ ] Reviewed architecture documentation
  - Notes: _____________

- [ ] Understood deployment process
  - Notes: _____________

### First Contributions
- [ ] Assigned first Linear task
  - Task ID: _____________
  - Description: _____________

- [ ] Created first feature branch
  - Branch name: _____________

- [ ] Made first commit
  - Commit hash: _____________
  - Date: _____________

- [ ] Created first Pull Request
  - PR number: #_____________
  - Status: [ ] Open [ ] Merged [ ] Closed

- [ ] Participated in code review
  - PR reviewed: #_____________

---

## Overall Experience

### What Went Well
<!-- Share what worked well in your onboarding process -->
Tutti disponibili

### Challenges Encountered
<!-- Share any difficulties or blockers you faced -->
Il non essere abituato al Mac 

### Suggestions for Improvement
<!-- How can we make onboarding better for future joiners? -->
Mettere una sezione key differences tra windows e mac
Forse va aggiornato

### Tools/Resources That Were Most Helpful
<!-- Which documentation or tools were particularly useful? -->
onboarding
Chatgpt

### Additional Notes
<!-- Any other feedback or comments -->

---

## Verification

### Final Checklist
- [ ] All development tools installed and working
- [ ] Can access all required platforms (Slack, Linear, AWS, GitHub)
- [ ] Successfully ran a Dataria project locally
- [ ] Created and merged at least one PR
- [ ] Completed security training (if required)
- [ ] Met with all key team members

### Sign-off

**New Joiner**: _____________
**Date Completed**: _____________
