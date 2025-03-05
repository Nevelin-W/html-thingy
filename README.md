# Static Website Deployment Workflow

## 🌐 Overview

This repository contains a GitHub Actions workflow and Terraform configuration for deploying a static website to AWS S3. The workflow provides flexible options to plan, apply, or destroy infrastructure using manual dispatch.

## 📋 Prerequisites

- GitHub account
- AWS Account
- Terraform installed
- AWS CLI configured

## 🛠 Workflow Components

### GitHub Actions Workflow (`webpage-setup.yml`)

The workflow supports three main actions:
- `plan`: Preview infrastructure changes
- `apply`: Deploy infrastructure and upload website files
- `destroy`: Remove infrastructure and empty S3 bucket

### Terraform Configuration

Creates an S3 bucket configured for static website hosting with public read access.

## 🚀 Setup Instructions

### 1. Repository Secrets

Configure the following secrets in your GitHub repository settings:

- `AWS_ACCESS_KEY_ID`: Your AWS access key
- `AWS_SECRET_ACCESS_KEY`: Your AWS secret access key
- `TF_API_TOKEN`: Terraform Cloud API token (if using Terraform Cloud)

### 2. Directory Structure

```
.
├── .github
│   └── workflows
│       └── webpage-setup.yml
├── terraform
│   └── main.tf
└── webpage
    └── index.html
```

### 3. Workflow Dispatch

Trigger the workflow manually from the GitHub Actions tab:
1. Select the workflow
2. Choose an action: plan, apply, or destroy
3. Run workflow

## 🔧 Workflow Details

### Environment Variables

- `AWS_REGION`: Configured as `eu-central-1`
- Terraform version: `1.11.0`

### Workflow Steps

1. Checkout repository
2. Setup Terraform
3. Configure AWS credentials
4. Initialize Terraform
5. Validate Terraform configuration
6. Perform selected action (plan/apply/destroy)
7. Upload/remove webpage files to/from S3

## 💡 S3 Bucket Configuration

- Public read access enabled
- Static website hosting configured
- Index document: `index.html`

## 📤 Outputs

After successful `apply`, the workflow will output the S3 website endpoint.
