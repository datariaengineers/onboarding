# macOS Development Setup

This guide covers the essential setup for macOS developers at Dataria.

## Prerequisites

Ensure you have admin access on your Mac and are connected to the internet.

## Package Manager Setup

### Homebrew Installation

**Homebrew** is the most popular package manager for macOS. It simplifies installing and managing software packages.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, add Homebrew to your PATH:
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### Verify Installation
```bash
brew --version
brew doctor
```

## Terminal Setup

### iTerm2 Installation

**iTerm2** is a powerful terminal replacement with advanced features like split panes, search, and extensive customization options.

```bash
brew install --cask iterm2
```

### iTerm2 Configuration

1. **Launch iTerm2** from Applications or Spotlight
2. **Color Scheme**: Go to Preferences > Profiles > Colors
   - Try "Solarized Dark" or "Tomorrow Night"
3. **Font Setup**: Preferences > Profiles > Text
   - Recommended fonts: "Fira Code", "JetBrains Mono", or "SF Mono"
   - Enable font ligatures if using Fira Code
4. **Shell Integration**: Install iTerm2 shell integration
   ```bash
   curl -L https://iterm2.com/shell_integration/install_shell_integration_and_utilities.sh | bash
   ```

### Optional: Oh My Zsh

**Oh My Zsh** enhances your terminal experience with themes and plugins.

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Popular plugins to add to `~/.zshrc`:
```bash
plugins=(git python terraform aws)
```

## Essential Development Tools

### Git (if not already installed)
```bash
brew install git
```

### Basic Configuration
```bash
# Configure Git with your details
git config --global user.name "Your Name"
git config --global user.email "your.email@dataria.com"
```

## Next Steps

After completing this macOS setup:

1. 🐍 [Set up Python Environment](./python-setup.md)
2. 🏗 [Install Terraform Tools](./terraform-setup.md)
3. ☁️ [Configure CLI Tools](./cli-tools.md)
4. 💻 [Choose your IDE](./ide-setup.md)

## Troubleshooting

### Common Issues

**Homebrew Installation Issues**:
- Ensure Xcode Command Line Tools are installed: `xcode-select --install`
- Check Apple Silicon vs Intel compatibility

**iTerm2 Not Opening**:
- Check System Preferences > Security & Privacy
- Allow applications downloaded from App Store and identified developers

**Permission Issues**:
- Some commands may require `sudo`
- Avoid using `sudo` with Homebrew installations

## Getting Help

- **Support**: #support on Slack
- **Homebrew Issues**: Check [brew.sh](https://brew.sh)
- **iTerm2 Help**: [iterm2.com/documentation.html](https://iterm2.com/documentation.html)