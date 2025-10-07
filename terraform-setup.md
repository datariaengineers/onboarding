# Terraform & Infrastructure as Code Setup

Terraform is our Infrastructure as Code (IaC) tool for managing AWS resources. It allows us to define, version control, and deploy infrastructure consistently across environments.

## What You'll Install

- **Terraform**: Infrastructure as Code tool for AWS resource management
- **tfenv**: Terraform version manager for project-specific versions
- **TFLint**: Terraform linter for catching errors and best practices

## Installation

### macOS Setup

#### 1. Install tfenv
**tfenv** manages multiple Terraform versions, similar to pyenv for Python.

```bash
brew install tfenv
```

#### 2. Install Terraform
```bash
# Install latest stable version
tfenv install latest

# Use the installed version
tfenv use latest

# Verify installation
terraform --version
```

#### 3. Install TFLint
```bash
# TFLint - Terraform linter
brew install tflint
```

### Windows Setup

#### 1. Install tfenv
```powershell
scoop bucket add main
scoop install tfenv
```

#### 2. Install Terraform
```powershell
# Install latest stable version
tfenv install latest
tfenv use latest

# Verify installation
terraform --version
```

#### 3. Install TFLint
```powershell
# TFLint
scoop install tflint
```

## Configuration

### TFLint Setup

Create a `.tflint.hcl` file in your project root for consistent linting:

```hcl
plugin "aws" {
  enabled = true
  version = "0.30.0"
  source  = "github.com/terraform-linters/tflint-ruleset-aws"
}

# Core Terraform rules
rule "terraform_deprecated_interpolation" {
  enabled = true
}

rule "terraform_unused_declarations" {
  enabled = true
}

rule "terraform_comment_syntax" {
  enabled = true
}

rule "terraform_documented_outputs" {
  enabled = true
}

rule "terraform_documented_variables" {
  enabled = true
}

# AWS-specific rules
rule "aws_instance_invalid_type" {
  enabled = true
}

rule "aws_route_not_specified_target" {
  enabled = true
}
```

### Pre-commit Hooks (Optional)

Set up pre-commit hooks for automatic code quality checks:

```bash
# Install pre-commit (if not already installed)
pip install pre-commit

# Create .pre-commit-config.yaml in project root
cat > .pre-commit-config.yaml << 'EOF'
repos:
  - repo: https://github.com/antonbabenko/pre-commit-terraform
    rev: v1.83.5
    hooks:
      - id: terraform_fmt
      - id: terraform_validate
      - id: terraform_tflint
EOF

# Install the hooks
pre-commit install
```

## Verification

Check all tools are working:

```bash
# Terraform version
terraform --version

# tfenv versions
tfenv list

# TFLint version
tflint --version
```

## Using Terraform Tools

### tfenv Commands

```bash
# List available Terraform versions
tfenv list-remote

# Install specific version
tfenv install 1.6.0

# Use specific version globally
tfenv use 1.6.0

# Use specific version for current directory
echo "1.6.0" > .terraform-version

# List installed versions
tfenv list
```

### Terraform Workflow

```bash
# Initialize Terraform (download providers)
terraform init

# Validate configuration
terraform validate

# Plan changes (dry run)
terraform plan

# Apply changes
terraform apply

# Destroy resources
terraform destroy
```

### Linting Workflow

```bash
# Format Terraform files
terraform fmt -recursive

# Run TFLint
tflint
```

## Project Structure Best Practices

Organize your Terraform projects like this:

```
terraform-project/
├── .terraform-version          # Pin Terraform version
├── .tflint.hcl                # TFLint configuration
├── main.tf                    # Main infrastructure definition
├── variables.tf               # Input variables
├── outputs.tf                 # Output values
├── versions.tf                # Provider version constraints
├── terraform.tfvars.example   # Example variable values
└── modules/                   # Reusable modules
    └── vpc/
        ├── main.tf
        ├── variables.tf
        └── outputs.tf
```

### Example versions.tf
```hcl
terraform {
  required_version = ">= 1.6.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```

## AWS Provider Configuration

Configure AWS provider for Terraform:

```hcl
# main.tf
provider "aws" {
  region = var.aws_region

  default_tags {
    tags = {
      Project     = "dataria"
      Environment = var.environment
      ManagedBy   = "terraform"
    }
  }
}
```

## Security Best Practices

1. **Never commit secrets**: Use AWS IAM roles or environment variables
2. **Use remote state**: Store Terraform state in S3 with DynamoDB locking
3. **Enable state encryption**: Encrypt state files at rest
4. **Review plans carefully**: Always review `terraform plan` before applying
5. **Use least privilege**: Grant minimal IAM permissions needed

### Example Backend Configuration
```hcl
terraform {
  backend "s3" {
    bucket         = "dataria-terraform-state"
    key            = "project/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks"
    encrypt        = true
  }
}
```

## Troubleshooting

### Common Issues

**Provider download issues**:
```bash
# Clear Terraform cache
rm -rf .terraform
terraform init
```

**State lock errors**:
```bash
# Force unlock (use carefully!)
terraform force-unlock <lock-id>
```

**Version conflicts**:
```bash
# Check current version
terraform --version

# Switch version
tfenv use 1.6.0
```

### TFLint Issues

**Plugin not found**:
```bash
# Install TFLint plugins
tflint --init
```

**Rule conflicts**:
- Check `.tflint.hcl` configuration
- Disable specific rules if needed

## Next Steps

With Terraform set up, proceed to:

1. ☁️ [Configure AWS & GitHub CLI](./cli-tools.md)
2. 💻 [Setup your IDE](./ide-setup.md) with Terraform extensions
3. ⚙️ [Apply configuration settings](./configuration.md)

## Getting Help

- **Support**: #support channel on Slack
- **Terraform Documentation**: [terraform.io/docs](https://terraform.io/docs)
- **AWS Provider**: [registry.terraform.io/providers/hashicorp/aws](https://registry.terraform.io/providers/hashicorp/aws)