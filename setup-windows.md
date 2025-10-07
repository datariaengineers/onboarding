# Windows Development Setup

This guide covers the essential setup for Windows developers at Dataria.

## Prerequisites

- Windows 10 or Windows 11
- Administrator access
- PowerShell 5.1 or newer

## Package Manager Setup

### Scoop Installation

**Scoop** is a command-line installer for Windows that keeps your system clean and organized by installing programs to user directories.

Open PowerShell and run:
```powershell
# Set execution policy (required for installation)
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

# Install Scoop
irm get.scoop.sh | iex
```

### Add Essential Buckets
```powershell
# Main bucket (already added by default)
scoop bucket add main

# Extras bucket for additional applications
scoop bucket add extras
```

### Verify Installation
```powershell
scoop --version
scoop list
```

## Terminal Setup

### Windows Terminal Installation

**Windows Terminal** is Microsoft's modern terminal application with tabs, themes, and extensive customization options.

```powershell
scoop install windows-terminal
```

### Windows Terminal Configuration

1. **Pin to Taskbar**: Right-click Windows Terminal and pin to taskbar
2. **Set as Default**: Settings > Startup > Default terminal application
3. **Install PowerShell 7** (optional but recommended):
   ```powershell
   scoop install pwsh
   ```

### Configuration Tips

1. **Open Settings**: Ctrl + Comma in Windows Terminal
2. **Themes**: Try "Campbell Powershell" or "Tango Dark"
3. **Font**: Set to "Cascadia Code" or install Fira Code:
   ```powershell
   scoop bucket add nerd-fonts
   scoop install FiraCode-NF
   ```

### Optional: PowerShell Profile

A PowerShell profile is a script that runs automatically when you start PowerShell. It's useful for setting aliases, functions, and environment variables.

#### Understanding PowerShell Profiles

PowerShell has different profile types. The most common is the **CurrentUser, CurrentHost** profile:

```powershell
# Check your profile path
$PROFILE

# Output example: C:\Users\YourName\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
# Or for PowerShell 5.1: C:\Users\YourName\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

#### Step-by-Step Profile Setup

1. **Check if profile exists**:
```powershell
Test-Path $PROFILE
# Returns True if exists, False if not
```

2. **View profile location**:
```powershell
# Display the full path to your profile
echo $PROFILE

# Display all profile paths
$PROFILE | Get-Member -MemberType NoteProperty
```

3. **Create profile if it doesn't exist**:
```powershell
# Create the profile file and any necessary parent directories
if (!(Test-Path $PROFILE)) {
    New-Item -Type File -Path $PROFILE -Force
    Write-Host "Profile created at: $PROFILE"
} else {
    Write-Host "Profile already exists at: $PROFILE"
}
```

4. **Edit your profile**:
```powershell
# Open in Notepad
notepad $PROFILE

# Or use VS Code (if installed)
code $PROFILE
```

#### Recommended Profile Content

Add this starter configuration to your profile:

```powershell
# PowerShell Profile for Dataria Development
# Location: $PROFILE

# ===== Execution Policy =====
# Ensure scripts can run (already set, but good to have)
# Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force

# ===== PSReadLine Configuration =====
# Enhanced command-line editing
if (Get-Module -ListAvailable -Name PSReadLine) {
    Import-Module PSReadLine
    Set-PSReadLineOption -PredictionSource History
    Set-PSReadLineOption -HistorySearchCursorMovesToEnd
    Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
    Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward
    Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete
}

# ===== Aliases =====
# Common Unix-like commands
Set-Alias -Name ll -Value Get-ChildItem
Set-Alias -Name grep -Value Select-String
Set-Alias -Name which -Value Get-Command

# Development shortcuts
Set-Alias -Name python -Value python3 -ErrorAction SilentlyContinue
Set-Alias -Name pip -Value pip3 -ErrorAction SilentlyContinue

# ===== Custom Functions =====
# Create directory and navigate into it
function mkcd {
    param([string]$path)
    New-Item -ItemType Directory -Path $path -Force | Out-Null
    Set-Location -Path $path
}

# Quick navigation to common directories
function docs { Set-Location ~\Documents }
function downloads { Set-Location ~\Downloads }
function desktop { Set-Location ~\Desktop }

# Git shortcuts
function gs { git status }
function gp { git pull }
function gps { git push }
function gc { git commit -m $args }

# ===== Environment Variables =====
# Add custom paths if needed
# $env:PATH += ";C:\Your\Custom\Path"

# ===== Welcome Message =====
Write-Host "Welcome to PowerShell, Dataria Developer!" -ForegroundColor Green
Write-Host "Profile loaded from: $PROFILE" -ForegroundColor Gray
```

5. **Reload your profile**:
```powershell
# After editing, reload the profile without restarting PowerShell
. $PROFILE

# Or use the shorter form
& $PROFILE
```

#### Verify Profile is Working

```powershell
# Test an alias
ll

# Test a function
mkcd test-folder

# Check if profile loaded
Write-Host "Profile location: $PROFILE"
```

#### Troubleshooting Profile Issues

**Profile not loading**:
```powershell
# Check execution policy
Get-ExecutionPolicy

# Should be RemoteSigned or Unrestricted
# If not, set it:
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Errors in profile**:
```powershell
# Test profile for syntax errors
Test-Path $PROFILE
Get-Content $PROFILE | ForEach-Object { $_ }

# Run profile manually to see errors
& $PROFILE
```

**Different PowerShell versions**:
- **PowerShell 5.1** (Windows PowerShell): `~\Documents\WindowsPowerShell\`
- **PowerShell 7+** (PowerShell Core): `~\Documents\PowerShell\`

Each has its own profile. If you use both, you may need to create profiles for each.

## Essential Development Tools

### Git Installation
```powershell
scoop install git
```

### Configure Git
```powershell
# Configure Git with your details
git config --global user.name "Your Name"
git config --global user.email "your.email@dataria.com"
```

### Windows Subsystem for Linux (Optional)

For developers who prefer Unix-like environments:

```powershell
# Enable WSL feature (requires restart)
wsl --install

# After restart, install Ubuntu
wsl --install -d Ubuntu
```

## Next Steps

After completing this Windows setup:

1. 🐍 [Set up Python Environment](./python-setup.md)
2. 🏗 [Install Terraform Tools](./terraform-setup.md)
3. ☁️ [Configure CLI Tools](./cli-tools.md)
4. 💻 [Choose your IDE](./ide-setup.md)

## Troubleshooting

### Common Issues

**Execution Policy Errors**:
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Scoop Installation Fails**:
- Ensure you have internet connection
- Run PowerShell as Administrator if needed
- Check Windows version compatibility

**Windows Terminal Won't Start**:
- Update Windows to latest version
- Install from Microsoft Store as alternative

**Path Issues**:
- Restart PowerShell after installations
- Check `$env:PATH` includes Scoop directories

## Getting Help

- **Support**: #support on Slack
- **Scoop Issues**: Check [scoop.sh](https://scoop.sh)
- **Windows Terminal**: [docs.microsoft.com/windows/terminal](https://docs.microsoft.com/windows/terminal)