# Configuration & Best Practices

Final configuration steps and recommended settings for optimal development experience at Dataria.

## Git Configuration

### Global Git Settings

Configure Git with your Dataria information:

```bash
# Set your identity
git config --global user.name "Your Full Name"
git config --global user.email "your.email@dataria.com"

# Set default branch name
git config --global init.defaultBranch main

# Improve Git output
git config --global color.ui auto
git config --global core.editor "code --wait"  # or vim, nano

# Better merge/diff tools
git config --global merge.tool vscode
git config --global diff.tool vscode
```

### Git Aliases for Productivity

```bash
# Useful shortcuts
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.pl pull
git config --global alias.ps push

# Advanced aliases
git config --global alias.lg "log --oneline --graph --decorate --all"
git config --global alias.last "log -1 HEAD"
git config --global alias.unstage "reset HEAD --"
```

### SSH Key Setup for GitHub

Generate SSH key for secure GitHub access:

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@dataria.com"

# Start SSH agent (macOS/Linux)
eval "$(ssh-agent -s)"

# Add key to SSH agent
ssh-add ~/.ssh/id_ed25519

# Copy public key to clipboard
# macOS:
pbcopy < ~/.ssh/id_ed25519.pub

# Windows:
clip < ~/.ssh/id_ed25519.pub

# Linux:
cat ~/.ssh/id_ed25519.pub
```

Add the public key to your GitHub account:
1. Go to GitHub.com > Settings > SSH and GPG keys
2. Click "New SSH key"
3. Paste your public key
4. Test connection: `ssh -T git@github.com`

## Shell Configuration

### Zsh Configuration (macOS)

Enhance your shell with useful configurations in `~/.zshrc`:

```bash
# Environment variables
export EDITOR="code --wait"
export BROWSER="open"

# Python/pyenv configuration
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# AWS CLI completion
autoload -U +X compinit && compinit
complete -C '/usr/local/bin/aws_completer' aws

# Terraform completion
autoload -U +X bashcompinit && bashcompinit
complete -o nospace -C /usr/local/bin/terraform terraform

# GitHub CLI completion
eval "$(gh completion --shell zsh)"

# Useful aliases
alias ll="ls -la"
alias la="ls -A"
alias l="ls -CF"
alias ..="cd .."
alias ...="cd ../.."

# Dataria-specific aliases
alias daws="aws --profile dataria"
alias tf="terraform"
alias tfa="terraform apply"
alias tfp="terraform plan"
alias python="python3"
alias pip="pip3"

# Functions
mkcd() { mkdir -p "$1" && cd "$1"; }
```

### PowerShell Profile (Windows)

Configure PowerShell profile for better experience:

```powershell
# Create/edit PowerShell profile
notepad $PROFILE

# Add to profile:
# Set execution policy for current user
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Import modules
Import-Module PSReadLine

# Set PSReadLine options
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward

# Aliases
Set-Alias -Name ll -Value Get-ChildItem
Set-Alias -Name la -Value Get-ChildItem
Set-Alias -Name python -Value python3
Set-Alias -Name pip -Value pip3

# Functions
function mkcd($dir) { mkdir $dir -force; cd $dir }
function tf { terraform $args }
function tfa { terraform apply $args }
function tfp { terraform plan $args }

# AWS CLI completion
Register-ArgumentCompleter -Native -CommandName aws -ScriptBlock {
    param($commandName, $wordToComplete, $cursorPosition)
    $env:COMP_LINE=$wordToComplete
    aws_completer.exe | ForEach-Object {
        [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
    }
}
```

## IDE Final Configuration

### VS Code User Settings

Add to VS Code User Settings (`Ctrl/Cmd + ,` > Open Settings JSON):

```json
{
  "editor.fontSize": 14,
  "editor.fontFamily": "'Fira Code', 'JetBrains Mono', Consolas, monospace",
  "editor.fontLigatures": true,
  "editor.tabSize": 4,
  "editor.insertSpaces": true,
  "editor.rulers": [88, 120],
  "editor.minimap.enabled": false,
  "editor.renderWhitespace": "boundary",
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,
  "workbench.colorTheme": "Dark+ (default dark)",
  "terminal.integrated.fontSize": 13,
  "git.autofetch": true,
  "git.confirmSync": false,
  "python.defaultInterpreterPath": "~/.pyenv/shims/python",
  "terraform.languageServer.enable": true,
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": true
    }
  },
  "[terraform]": {
    "editor.defaultFormatter": "hashicorp.terraform",
    "editor.formatOnSave": true
  },
  "aws.telemetry": false
}
```

### Project Template

Create a template structure for new projects:

```
dataria-project-template/
├── .gitignore
├── .python-version
├── .terraform-version
├── .editorconfig
├── .pre-commit-config.yaml
├── README.md
├── requirements.txt
├── pyproject.toml
├── .vscode/
│   └── settings.json
└── infrastructure/
    ├── main.tf
    ├── variables.tf
    ├── outputs.tf
    └── .tflint.hcl
```

#### .gitignore Template
```gitignore
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
venv/
.venv/
pip-log.txt
pip-delete-this-directory.txt

# Terraform
.terraform/
*.tfstate
*.tfstate.*
.terraform.lock.hcl

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# AWS
.aws/

# Environment variables
.env
.env.local
```

#### pyproject.toml Template
```toml
[tool.black]
line-length = 88
target-version = ['py312']
include = '\.pyi?$'

[tool.isort]
profile = "black"
line_length = 88
multi_line_output = 3

[tool.pylint]
max-line-length = 88
disable = ["C0114", "C0116"]  # Missing docstrings

[tool.mypy]
python_version = "3.12"
warn_return_any = true
warn_unused_configs = true
```

## Environment Variables

### Development Environment

Create a `.env.template` file for projects:

```bash
# AWS Configuration
AWS_DEFAULT_REGION=us-east-1
AWS_PROFILE=dataria

# Application Settings
DEBUG=true
LOG_LEVEL=INFO

# Database (example)
# DATABASE_URL=postgresql://localhost:5432/dataria_dev

# External APIs
# API_BASE_URL=https://api.dataria.com
# API_KEY=your-api-key-here
```

### Shell Environment

Add to your shell configuration:

```bash
# Development environment
export DATARIA_ENV=development
export LOG_LEVEL=INFO

# Python
export PYTHONPATH="${PYTHONPATH}:${PWD}"
export PIPENV_VENV_IN_PROJECT=1

# AWS
export AWS_DEFAULT_REGION=us-east-1
export AWS_PAGER=""  # Disable pager for AWS CLI

# Terraform
export TF_VAR_environment=dev
```

## Quality Assurance Setup

### Pre-commit Hooks

Install pre-commit for automatic code quality checks:

```bash
# Install pre-commit
pip install pre-commit

# Create .pre-commit-config.yaml
cat > .pre-commit-config.yaml << 'EOF'
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-merge-conflict
      - id: check-yaml

  - repo: https://github.com/psf/black
    rev: 23.3.0
    hooks:
      - id: black

  - repo: https://github.com/pycqa/isort
    rev: 5.12.0
    hooks:
      - id: isort

  - repo: https://github.com/antonbabenko/pre-commit-terraform
    rev: v1.83.5
    hooks:
      - id: terraform_fmt
      - id: terraform_validate
      - id: terraform_tflint
EOF

# Install hooks
pre-commit install
```

## Security Best Practices

### Credential Management

1. **Never commit secrets**:
   - Use `.env` files (add to `.gitignore`)
   - Use AWS Parameter Store or Secrets Manager
   - Use environment variables

2. **AWS Security**:
   - Enable MFA on AWS account
   - Use IAM roles instead of access keys when possible
   - Rotate access keys regularly

3. **SSH Security**:
   - Use SSH keys instead of passwords
   - Add passphrase to SSH keys
   - Use different keys for different services

### Code Security

Follow security best practices in your code:
- Never commit secrets or credentials
- Use environment variables for sensitive data
- Review code for security vulnerabilities during PR reviews
- Keep dependencies up to date
- Use linting tools to catch common security issues

## Verification Checklist

Verify your complete setup:

```bash
# Check versions
python --version
terraform --version
aws --version
gh --version
code --version

# Test Git
git config --list | grep user
ssh -T git@github.com

# Test AWS
aws sts get-caller-identity

# Test GitHub
gh auth status

# Test Terraform
terraform --version
tflint --version

# Test Python tools
uv --version
black --version
```

## Next Steps

🎉 **Congratulations!** Your development environment is now complete.

### What's Next:
1. **Clone a project**: `gh repo clone datariaengineers/your-first-project`
2. **Join team channels**: Check Slack for project-specific channels
3. **Review documentation**: Look for project-specific README files


## Getting Help

- **General Questions**: #general on Slack
- **Your Manager**: Direct message for role-specific questions

Welcome to the Dataria engineering team! 🚀