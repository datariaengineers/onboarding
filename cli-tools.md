# CLI Tools: AWS & GitHub

Command-line interfaces for our core platforms enable efficient workflow automation and quick access to cloud resources and version control operations.

## What You'll Install

- **AWS CLI**: Command-line interface for Amazon Web Services
- **GitHub CLI (gh)**: Command-line interface for GitHub operations

## Installation

### macOS Setup

```bash
# AWS CLI
brew install awscli

# GitHub CLI
brew install gh
```

### Windows Setup

```powershell
# AWS CLI
scoop install aws

# GitHub CLI
scoop install gh
```

## Configuration

### AWS CLI Setup

**AWS CLI** provides direct access to AWS services from your terminal, essential for managing cloud resources and debugging.

#### 1. Configure AWS Credentials
```bash
# Interactive configuration
aws configure

# You'll be prompted for:
# - AWS Access Key ID: (get from your manager)
# - AWS Secret Access Key: (get from your manager)
# - Default region: us-east-1 (or your preferred region)
# - Default output format: json
```

#### 2. Verify Configuration
```bash
# Test your credentials
aws sts get-caller-identity

# Should output your AWS account details
```

#### 3. Additional Configuration
```bash
# Set up named profiles for different environments
aws configure --profile staging
aws configure --profile production

# Use a specific profile
aws s3 ls --profile staging
```

### GitHub CLI Setup

**GitHub CLI** streamlines Git operations, PR management, and repository interactions directly from the terminal.

#### 1. Authenticate
```bash
# Login to GitHub
gh auth login

# Follow the prompts:
# - Choose GitHub.com
# - Choose HTTPS or SSH (HTTPS is easier)
# - Authenticate via web browser (recommended)
```

#### 2. Verify Authentication
```bash
# Check authentication status
gh auth status

# Should show your GitHub username and scopes
```

#### 3. Configure Default Editor
```bash
# Set VS Code as default editor
gh config set editor "code --wait"

# Or for other editors:
# gh config set editor "vim"
# gh config set editor "nano"
```

## Using CLI Tools

### AWS CLI Common Commands

```bash
# S3 operations
aws s3 ls                              # List buckets
aws s3 ls s3://bucket-name            # List objects in bucket
aws s3 cp file.txt s3://bucket/       # Upload file
aws s3 sync ./local-folder s3://bucket/folder/  # Sync directory

# EC2 operations
aws ec2 describe-instances            # List EC2 instances
aws ec2 describe-security-groups      # List security groups
aws ec2 describe-vpcs                 # List VPCs

# IAM operations
aws iam list-users                    # List IAM users
aws iam get-user                      # Get current user info

# CloudFormation/Terraform state
aws s3 ls s3://dataria-terraform-state/  # Check Terraform state

# Logs
aws logs describe-log-groups          # List CloudWatch log groups
aws logs tail /aws/lambda/function-name --follow  # Tail logs
```

### GitHub CLI Common Commands

```bash
# Repository operations
gh repo clone datariaengineers/repo-name     # Clone repository
gh repo create my-new-repo                   # Create new repository
gh repo view                                 # View current repository
gh repo list datariaengineers                # List organization repos

# Pull request operations
gh pr create --title "Fix bug" --body "Description"  # Create PR
gh pr list                                   # List PRs
gh pr view 123                              # View PR details
gh pr checkout 123                          # Checkout PR branch
gh pr merge 123                             # Merge PR

# Issue operations
gh issue create --title "Bug report"        # Create issue
gh issue list                               # List issues
gh issue view 45                            # View issue details
gh issue close 45                           # Close issue

# Workflow operations
gh workflow list                            # List GitHub Actions
gh workflow run deploy.yml                 # Trigger workflow
gh run list                                 # List workflow runs
gh run view 123456                         # View run details
```

### Advanced Usage

#### AWS CLI with Terraform
```bash
# Get Terraform backend info
aws s3 ls s3://dataria-terraform-state/

# Check DynamoDB locks
aws dynamodb scan --table-name terraform-locks

# Assume IAM role for cross-account access
aws sts assume-role --role-arn arn:aws:iam::123456789012:role/DevRole --role-session-name dev-session
```

#### GitHub CLI for Team Collaboration
```bash
# Review PRs efficiently
gh pr list --assignee @me              # PRs assigned to you
gh pr review 123 --approve             # Approve PR
gh pr review 123 --request-changes     # Request changes

# Work with Linear integration
gh issue create --title "Linear: DATA-123"  # Reference Linear issue

# Bulk operations
gh pr list --json number | jq '.[].number' | xargs -I {} gh pr view {}
```

## Configuration Files

### AWS CLI Configuration

AWS CLI stores configuration in `~/.aws/`:

```bash
# View configuration
cat ~/.aws/config
cat ~/.aws/credentials

# Example ~/.aws/config
[default]
region = us-east-1
output = json

[profile staging]
region = us-east-1
output = json

[profile production]
region = us-east-1
output = json
```

### GitHub CLI Configuration

GitHub CLI stores configuration in your system's config directory:

```bash
# View configuration
gh config list

# Common configurations
gh config set git_protocol https
gh config set editor "code --wait"
gh config set prompt enabled
```

## Security Best Practices

### AWS CLI Security
1. **Use IAM roles**: Prefer IAM roles over access keys when possible
2. **Rotate credentials**: Regularly rotate access keys
3. **Least privilege**: Request minimal permissions needed
4. **Multi-factor authentication**: Enable MFA on your AWS account
5. **Named profiles**: Use different profiles for different environments

### GitHub CLI Security
1. **Token scopes**: Review and limit GitHub token permissions
2. **Regular audits**: Periodically check `gh auth status`
3. **Secure storage**: GitHub CLI stores tokens securely in your system keychain

## Troubleshooting

### AWS CLI Issues

**Credentials not found**:
```bash
# Check configuration
aws configure list

# Verify credentials file
cat ~/.aws/credentials

# Test with specific profile
aws sts get-caller-identity --profile staging
```

**Region issues**:
```bash
# Set region explicitly
aws configure set region us-east-1

# Or use environment variable
export AWS_DEFAULT_REGION=us-east-1
```

### GitHub CLI Issues

**Authentication failed**:
```bash
# Re-authenticate
gh auth logout
gh auth login

# Check authentication
gh auth status
```

**Repository not found**:
```bash
# Ensure you have access to datariaengineers organization
gh repo list datariaengineers

# Clone with full URL if needed
gh repo clone https://github.com/datariaengineers/repo-name
```

## Verification

Test all CLI tools are working:

```bash
# AWS CLI
aws --version
aws sts get-caller-identity

# GitHub CLI
gh --version
gh auth status
gh repo list datariaengineers --limit 5
```

## Next Steps

With CLI tools configured, proceed to:

1. 💻 [Setup your IDE](./ide-setup.md) with integration features
2. ⚙️ [Apply configuration settings](./configuration.md) for optimal workflow

## Getting Help

- **AWS CLI Issues**: #devops channel on Slack
- **GitHub CLI Issues**: #tech channel on Slack
- **AWS CLI Documentation**: [docs.aws.amazon.com/cli](https://docs.aws.amazon.com/cli)
- **GitHub CLI Documentation**: [cli.github.com](https://cli.github.com)