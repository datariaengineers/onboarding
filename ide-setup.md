# IDE & Editor Setup

Choose your development environment from our recommended editors. All options provide excellent support for Python, Terraform, and our development workflow.

## IDE Options

### Option 1: Visual Studio Code (Recommended)

**VS Code** is a lightweight, extensible code editor with excellent Python and Terraform support, integrated terminal, and rich ecosystem.

#### Installation

**macOS:**
```bash
brew install --cask visual-studio-code
```

**Windows:**
```powershell
scoop bucket add extras
scoop install vscode
```

#### Essential Extensions

Install these extensions for optimal Dataria development:

```bash
# Core Python development
code --install-extension ms-python.python
code --install-extension ms-python.black-formatter
code --install-extension ms-python.isort
code --install-extension ms-python.pylint

# Terraform support
code --install-extension hashicorp.terraform

# General development
code --install-extension ms-vscode.vscode-json
code --install-extension ms-toolsai.jupyter
code --install-extension GitLens

# AWS integration
code --install-extension amazonwebservices.aws-toolkit-vscode

# GitHub integration
code --install-extension GitHub.vscode-pull-request-github
```

#### VS Code Configuration

Create `.vscode/settings.json` in your project root:

```json
{
  "python.defaultInterpreterPath": "~/.pyenv/shims/python",
  "python.formatting.provider": "none",
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": true
    }
  },
  "terraform.languageServer.enable": true,
  "terraform.codelens.referenceCount": true,
  "editor.formatOnSave": true,
  "files.trimTrailingWhitespace": true,
  "files.insertFinalNewline": true,
  "editor.rulers": [88, 120],
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": true
}
```

### Option 2: PyCharm Community Edition

**PyCharm Community** is JetBrains' free Python IDE with powerful debugging, refactoring, and code intelligence features.

#### Installation

**macOS:**
```bash
brew install --cask pycharm-ce
```

**Windows:**
```powershell
scoop bucket add extras
scoop install pycharm-community
```

#### Configuration

1. **Python Interpreter**: Settings > Project > Python Interpreter
   - Select your pyenv Python installation
   - Usually located at `~/.pyenv/versions/3.12.0/bin/python`

2. **Terraform Plugin**: Settings > Plugins
   - Search for "Terraform and HCL"
   - Install and restart PyCharm

3. **Code Style**: Settings > Editor > Code Style > Python
   - Set line length to 88 (Black standard)
   - Enable "Optimize imports on the fly"

4. **AWS Integration**: Settings > Plugins
   - Search for "AWS Toolkit"
   - Install for AWS resource management

### Option 3: Claude Code (AI Assistant)

**Claude Code** is Anthropic's AI-powered development assistant that integrates with your terminal and workflow.

#### Installation

**macOS:**
```bash
brew install anthropics/claude/claude
```

**Windows:**
```powershell
# Requires Node.js
scoop install nodejs
npm install -g @anthropic-ai/claude-code
```

#### Setup

```bash
# Authenticate with Anthropic
claude auth

# Configure preferences
claude config

# Test installation
claude --version
```

#### Usage Examples

```bash
# Start interactive chat
claude chat

# AI-assisted file editing
claude edit main.py

# Code review
claude review --diff

# Generate documentation
claude docs generate

# Explain code
claude explain complex_function.py:42-67
```

## Editor Features & Workflows

### VS Code Workflow

1. **Integrated Terminal**: Use Ctrl/Cmd + ` to open terminal
2. **Command Palette**: Ctrl/Cmd + Shift + P for quick actions
3. **File Explorer**: Ctrl/Cmd + Shift + E
4. **Source Control**: Ctrl/Cmd + Shift + G for Git operations
5. **Extensions**: Ctrl/Cmd + Shift + X to manage extensions

### PyCharm Workflow

1. **Project Navigation**: Ctrl/Cmd + E for recent files
2. **Search Everywhere**: Double Shift for global search
3. **Refactoring**: Right-click > Refactor for code improvements
4. **Debugging**: Set breakpoints and use F5 to debug
5. **Version Control**: VCS menu for Git operations

### Claude Code Integration

Claude Code works alongside any editor:

```bash
# Review changes before committing
claude review

# Get help with error messages
claude explain "ImportError: No module named 'boto3'"

# Generate tests
claude generate tests for data_processor.py

# Optimize code
claude optimize --performance main.py
```

## Project Configuration

### Workspace Settings

Create project-specific configurations:

#### VS Code Workspace (`.vscode/settings.json`)
```json
{
  "python.defaultInterpreterPath": "./.venv/bin/python",
  "terraform.languageServer.rootModules": ["./infrastructure"],
  "files.associations": {
    "*.tf": "terraform",
    "*.tfvars": "terraform"
  }
}
```

#### PyCharm Project Settings
- **Project Structure**: Mark directories as sources/tests
- **Run Configurations**: Set up common tasks
- **External Tools**: Configure Terraform, AWS CLI shortcuts

### EditorConfig

Create `.editorconfig` for consistent formatting across editors:

```ini
root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
indent_style = space
indent_size = 4

[*.{py}]
max_line_length = 88

[*.{tf,tfvars}]
indent_size = 2

[*.{yml,yaml}]
indent_size = 2

[*.{json}]
indent_size = 2
```

## Productivity Tips

### VS Code Tips
- **Multi-cursor editing**: Alt + Click or Ctrl/Cmd + D
- **Zen mode**: Ctrl/Cmd + K, Z for distraction-free coding
- **Split editor**: Ctrl/Cmd + \ for side-by-side editing
- **Integrated Git**: Use source control panel for visual Git operations

### PyCharm Tips
- **Live templates**: Create code snippets for common patterns
- **Database tools**: Connect to AWS RDS instances directly
- **TODO tracking**: Automatic tracking of TODO comments
- **Profiler**: Built-in Python profiler for performance analysis

### Claude Code Tips
- **Context aware**: Claude understands your project structure
- **Iterative improvement**: Ask follow-up questions for refinement
- **Multi-file operations**: Can work across multiple files simultaneously
- **Learning tool**: Great for understanding complex codebases

## Troubleshooting

### VS Code Issues

**Python interpreter not found**:
```bash
# Check pyenv path
which python

# In VS Code: Ctrl/Cmd + Shift + P > "Python: Select Interpreter"
```

**Extensions not working**:
- Reload window: Ctrl/Cmd + R
- Check extension logs in Output panel
- Disable conflicting extensions

### PyCharm Issues

**Slow performance**:
- Increase memory: Help > Change Memory Settings
- Exclude large directories from indexing
- Disable unused plugins

**Python interpreter issues**:
- File > Settings > Project > Python Interpreter
- Click gear icon > Add > System Interpreter
- Point to pyenv Python installation

### Claude Code Issues

**Authentication problems**:
```bash
# Re-authenticate
claude auth logout
claude auth login
```

**Context not working**:
```bash
# Refresh project context
claude index refresh
```

## Next Steps

With your IDE set up, proceed to:

1. ⚙️ [Apply final configuration settings](./configuration.md)
2. 📋 Clone your first Dataria repository
3. 🚀 Start contributing to projects!

## Getting Help

- **VS Code Issues**: #tech channel on Slack
- **PyCharm Issues**: #tech channel on Slack
- **Claude Code Issues**: #general channel on Slack
- **VS Code Documentation**: [code.visualstudio.com/docs](https://code.visualstudio.com/docs)
- **PyCharm Documentation**: [jetbrains.com/help/pycharm](https://www.jetbrains.com/help/pycharm/)