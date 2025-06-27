# Terraform S3 Bucket Automation

This repository contains Terraform configuration to create an Amazon S3 bucket, with automation via GitHub Actions.

## Project Structure

```
terraform-s3-automation/
├── main.tf                # S3 bucket resource definition
├── provider.tf            # AWS provider configuration
├── variables.tf           # Input variables (bucket name, region)
├── terraform.tfvars       # Variable values for deployment
├── outputs.tf             # Output values
├── .gitignore             # Ignore Terraform state and sensitive files
└── .github/workflows/
    └── terraform.yml      # GitHub Actions workflow for automated deployment
```

## What It Does

- Provisions a single Amazon S3 bucket using Terraform
- Only `bucket_name` and `aws_region` are configurable via variables
- All tags and other settings are hardcoded for simplicity
- Automatically runs `terraform init`, `plan`, and `apply` on GitHub push to `main` branch

## Prerequisites

- Terraform installed (for local testing)
- AWS IAM user with permissions to create S3 buckets
- AWS credentials set as GitHub secrets:
  - `AWS_ACCESS_KEY_ID`
  - `AWS_SECRET_ACCESS_KEY`

## Usage

### 1. Clone this Repository

```bash
git clone https://github.com/your-username/terraform-s3-automation.git
cd terraform-s3-automation
```

### 2. Update `terraform.tfvars`

```hcl
bucket_name = "your-unique-s3-bucket-name"
aws_region  = "us-east-1"
```

### 3. Commit and Push to GitHub

Pushing to the `main` branch will trigger the GitHub Actions workflow to apply the Terraform configuration.

### 4. (Optional) Run Locally

```bash
terraform init
terraform plan -var-file="terraform.tfvars"
terraform apply -auto-approve -var-file="terraform.tfvars"
```

## Download

You can download this project as a ZIP:
[Download ZIP](https://github.com/your-username/terraform-s3-automation/archive/refs/heads/main.zip)
