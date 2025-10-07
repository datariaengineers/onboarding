# Dataria Onboarding Guide

Welcome to Dataria! This comprehensive onboarding guide will help you set up your development environment and understand our tech stack.

## 📋 Quick Start Checklist

### Day 1 - Essential Access
- [ ] **Dataria Slack** - Team communication platform
- [ ] **Linear** - Agile project management and issue tracking
- [ ] **AWS Console** - Cloud infrastructure access
- [ ] **GitHub** - Code repository access to https://github.com/datariaengineers
- [ ] **Company email** - Corporate email account

### First Week
- [ ] Join relevant Slack channels
- [ ] Get added to appropriate Linear teams
- [ ] Verify AWS permissions for your role
- [ ] Clone necessary repositories from GitHub
- [ ] Complete security training

## 🛠 Development Environment Setup

Choose your platform and follow the detailed setup guides:

### Platform Setup
- [🍎 macOS Setup](./setup-macos.md) - Package managers, terminals, and basic tools
- [🪟 Windows Setup](./setup-windows.md) - Package managers, terminals, and basic tools

### Development Stacks
- [🐍 Python Environment](./python-setup.md) - Python version management and package tools
- [🏗 Terraform Setup](./terraform-setup.md) - Infrastructure as Code tools and linting
- [☁️ AWS & GitHub CLI](./cli-tools.md) - Cloud and version control command line tools

### IDEs & Editors
- [💻 IDE Setup](./ide-setup.md) - VS Code, PyCharm, and Claude Code installation
- [⚙️ Configuration Tips](./configuration.md) - Recommended settings and extensions

## 🔧 Our Tech Stack

### Core Technologies

#### **Python** 🐍
Our primary programming language for data processing, web applications, and automation scripts. We use modern Python practices with type hints and async programming.

#### **Terraform** 🏗
Infrastructure as Code tool for managing AWS resources. Allows us to version control our infrastructure and deploy consistently across environments.

#### **AWS** ☁️
Our cloud platform for hosting applications, data storage, and compute resources. We use services like EC2, S3, RDS, Lambda, and more.

### Development Tools

#### **pyenv** 🔄
Python version manager that allows switching between different Python versions per project, ensuring consistent development environments.

#### **uv** ⚡
Ultra-fast Python package installer and resolver. Modern replacement for pip that speeds up dependency management significantly.

#### **tfenv** 🔄
Terraform version manager for switching between Terraform versions, ensuring compatibility across different projects.

### Quality & Linting Tools

#### **TFLint** ✅
Terraform linter that catches errors, warns about deprecated syntax, and enforces best practices for infrastructure code.

#### **Black & isort** 🎨
Python code formatters that ensure consistent code style across the team, automatically formatting code on save.

### Productivity Tools

#### **Linear** 📊
Modern project management tool for agile development. Tracks issues, sprints, and project progress with excellent GitHub integration.

#### **GitHub CLI (gh)** 🐙
Command-line interface for GitHub operations. Create PRs, manage issues, and interact with repositories without leaving the terminal.

#### **AWS CLI** 🖥
Command-line interface for AWS services. Deploy resources, manage configurations, and debug issues directly from the terminal.

#### **Claude Code** 🤖
AI-powered coding assistant that helps with code review, debugging, refactoring, and learning new technologies.

## ✅ Your Onboarding Checklist

**Important**: As you go through this onboarding process, you'll create a personal checklist and submit it as a Pull Request!

### Why Create a Checklist?
1. **Track your progress** through setup
2. **Document your experience** to help future joiners
3. **Learn Git/GitHub workflow** hands-on
4. **Share feedback** to improve onboarding

### How to Start
1. Go to [onboarding/](./onboarding/) directory
2. Copy the `TEMPLATE.md` to `onboarding/checklists/your-name.md`
3. Check off items as you complete them
4. Add notes about issues and solutions
5. Create a Pull Request when done

📖 **See [onboarding/README.md](./onboarding/README.md) for detailed instructions**

This will be your **first contribution** to Dataria's codebase! 🎉

## 📂 File Structure

```
docs/
├── README.md              # This file - main onboarding guide
├── setup-macos.md         # macOS-specific setup instructions
├── setup-windows.md       # Windows-specific setup instructions
├── python-setup.md        # Python development environment
├── terraform-setup.md     # Terraform and IaC tools
├── cli-tools.md          # AWS CLI, GitHub CLI setup
├── ide-setup.md          # IDEs and editors installation
├── configuration.md      # Settings and configuration tips
└── onboarding/           # Onboarding checklist process
    ├── README.md         # Checklist instructions
    ├── TEMPLATE.md       # Your checklist template
    └── checklists/       # Completed checklists from team
```

## 👥 Key Contacts

- **Direct Manager**: Azzurra Roberto, azzurra@dataria.it
- **Support**: #support on Slack

## 🆘 Getting Help

1. **First**: Check the relevant documentation file
2. **Then**: Ask in appropriate Slack channels
3. **If needed**: Contact your manager or team lead
4. **Always**: Don't hesitate to ask questions!

## 🎯 Next Steps

### Start Your Onboarding Journey

1. **Create your checklist**: Copy [onboarding/TEMPLATE.md](./onboarding/TEMPLATE.md) to track your progress
2. Complete platform setup ([macOS](./setup-macos.md) or [Windows](./setup-windows.md))
3. Set up [Python environment](./python-setup.md)
4. Install [Terraform tools](./terraform-setup.md)
5. Configure [CLI tools](./cli-tools.md)
6. Choose and setup your [IDE](./ide-setup.md)
7. Apply [configuration settings](./configuration.md)
8. **Submit your checklist PR**: Share your experience and make your first contribution!

📋 **Remember**: Track everything in your [onboarding checklist](./onboarding/README.md) and create a PR when done!

Welcome to the Dataria team! 🎉