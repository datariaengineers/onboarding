# Python Development Environment

Python is our primary programming language at Dataria for data processing, web applications, and automation. This guide covers setting up a modern Python development environment.

## What You'll Install

- **pyenv**: Python version manager for switching between Python versions
- **uv**: Ultra-fast Python package installer and dependency resolver
- **Python 3.12**: Latest stable Python version with modern features

## Installation

### macOS Setup

#### 1. Install pyenv
**pyenv** allows you to install and switch between multiple Python versions easily.

```bash
brew install pyenv
```

#### 2. Configure Shell Integration
Add pyenv to your shell configuration:

```bash
# For Zsh (default on macOS)
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc

# Reload your shell
source ~/.zshrc
```

#### 3. Install Python
```bash
# Install Python 3.12 (adjust version as needed)
pyenv install 3.12.0

# Set as global default
pyenv global 3.12.0

# Verify installation
python --version
```

#### 4. Install uv
**uv** is a fast Python package installer that's 10-100x faster than pip.

```bash
brew install uv
```

### Windows Setup

#### 1. Install pyenv-win
```powershell
scoop install pyenv
```

#### 2. Install Python
```powershell
# Install Python 3.12
pyenv install 3.12.0

# Set as global default
pyenv global 3.12.0

# Verify installation
python --version
```

#### 3. Install uv
```powershell
scoop install uv
```

## Verification

Check that everything is working correctly:

```bash
# Check Python version
python --version
# Should output: Python 3.12.0

# Check pyenv
pyenv versions
# Should show installed Python versions with * next to active one

# Check uv
uv --version
# Should output uv version information

# Check pip (comes with Python)
pip --version
```

## Using Python Tools

### pyenv Commands

```bash
# List available Python versions
pyenv install --list

# Install a specific Python version
pyenv install 3.11.5

# List installed versions
pyenv versions

# Switch global Python version
pyenv global 3.11.5

# Set Python version for current directory
pyenv local 3.12.0

# Show current Python version
pyenv version
```

### uv Commands

```bash
# Create a new virtual environment
uv venv myproject

# Activate virtual environment (macOS/Linux)
source myproject/bin/activate

# Activate virtual environment (Windows)
myproject\Scripts\activate

# Install packages (much faster than pip)
uv pip install requests pandas numpy

# Install from requirements.txt
uv pip install -r requirements.txt

# Sync dependencies (like pip-sync)
uv pip sync requirements.txt
```

## Project Setup Best Practices

### 1. Use Virtual Environments
Always create isolated environments for your projects:

```bash
# Navigate to your project directory
cd my-dataria-project

# Create virtual environment
uv venv .venv

# Activate it
source .venv/bin/activate  # macOS/Linux
# or
.venv\Scripts\activate     # Windows

# Install project dependencies
uv pip install -r requirements.txt
```

### 2. Pin Python Version
Create a `.python-version` file in your project root:

```bash
echo "3.12.0" > .python-version
```

This ensures everyone uses the same Python version for the project.

### 3. Manage Dependencies
Create and maintain a `requirements.txt` file:

```bash
# Generate requirements from current environment
uv pip freeze > requirements.txt

# Install from requirements
uv pip install -r requirements.txt
```

## Common Python Tools for Data Work

After setting up Python, you might want to install these common packages:

```bash
# Data science essentials
uv pip install pandas numpy matplotlib seaborn jupyter

# Web development
uv pip install fastapi uvicorn pydantic

# AWS integration
uv pip install boto3 awscli

# Testing
uv pip install pytest pytest-cov

# Code quality
uv pip install black isort flake8 mypy
```

## Troubleshooting

### pyenv Issues

**Python version not switching**:
```bash
# Ensure shell integration is working
which python
# Should point to pyenv shims directory

# Rehash if needed
pyenv rehash
```

**Build dependencies missing (macOS)**:
```bash
# Install required build tools
brew install openssl readline sqlite3 xz zlib
```

### uv Issues

**Command not found**:
- Ensure package manager PATH is correctly set
- Restart terminal after installation

**Permission errors**:
- Use virtual environments instead of global installations
- Avoid `sudo` with uv commands

## Next Steps

With Python set up, proceed to:

1. 🏗 [Install Terraform Tools](./terraform-setup.md)
2. ☁️ [Configure CLI Tools](./cli-tools.md)
3. 💻 [Setup your IDE](./ide-setup.md) with Python extensions

## Getting Help

- **Python Issues**: #tech channel on Slack
- **pyenv Documentation**: [github.com/pyenv/pyenv](https://github.com/pyenv/pyenv)
- **uv Documentation**: [github.com/astral-sh/uv](https://github.com/astral-sh/uv)