# 🚀 Terraform - AWS Cloud Infrastructure: Zero to Hero

Welcome to the Zero to Hero guide on Terraform for provisioning and managing AWS Cloud Infrastructure. This repository takes you through every step, from setting up your environment to mastering advanced Terraform features.

## 📖 Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Installing Tools](#installing-tools)
  - [Setting Up AWS Credentials](#setting-up-aws-credentials)
- [Terraform Basics](#terraform-basics)
  - [Providers, Resources, and Variables](#providers-resources-and-variables)
  - [State Files and Backend](#state-files-and-backend)
- [Project Walkthrough](#project-walkthrough)
  - [Step-by-Step Implementation](#step-by-step-implementation)
- [Advanced Topics](#advanced-topics)
  - [Remote State Management](#remote-state-management)
  - [Terraform Modules](#terraform-modules)
  - [Managing Multiple Environments](#managing-multiple-environments)
- [Best Practices](#best-practices)
- [Clean Up](#clean-up)
- [Resources](#resources)

---

## 📝 Introduction

Terraform is an open-source tool that uses Infrastructure as Code (IaC) to define, provision, and manage cloud infrastructure. This guide focuses on provisioning an EC2 instance on AWS, expanding into advanced Terraform features as you progress.

---

## 📋 Prerequisites

Ensure you have the following installed and configured:
- **Terraform**: [Install Terraform](https://developer.hashicorp.com/terraform/downloads)
- **AWS CLI**: [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- **AWS Account**: [Sign up for an AWS account](https://aws.amazon.com/)
- **Text Editor/IDE**: Visual Studio Code is recommended.

---

## 💻 Getting Started

### 1. Installing Tools

Install Terraform:
```bash
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```


Install AWS CLI: Follow the official AWS CLI installation guide.
Verify installations:
```bash
terraform -v
aws --version
```

### 2. Setting Up AWS Credentials
Run:
```bash
aws configure
```
Provide:
- AWS Access Key
- AWS Secret Key
- Default region (e.g., us-east-1)
- Output format (e.g., json)

## 🚀 Terraform Basics
### 1. Providers
Providers define the cloud service (e.g., AWS). Example:
```hcl

provider "aws" {
  region = "us-east-1"
}
```
### 2. Resources
Resources define specific infrastructure components. Example:
```hcl
Copy code
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
```
### 3. Variables
Variables make configurations reusable and manageable. Example:
```hcl
variable "instance_type" {
  default = "t2.micro"
}
```
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}

### 4. State Files
Terraform keeps track of the infrastructure state. Never manually edit terraform.tfstate.

## 🔨 Project Walkthrough
### Step 1: Initialize the Project
```bash
terraform init
```
### Step 2: Define Infrastructure
Create a main.tf file with the following:
```hcl
provider "aws" {
  region = "us-east-1"
}
```
resource "aws_instance" "my_instance" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "MyFirstInstance"
  }
}

### Step 3: Validate and Plan
```bash
terraform validate
terraform plan
```
### Step 4: Apply Changes
```bash
terraform apply
```
Confirm the changes, and Terraform will provision the resources.
### Step 5: View Outputs
```hcl
output "instance_id" {
  value = aws_instance.my_instance.id
}
```
Run:
```bash
terraform output
```

## 🌟 Advanced Topics
### 1. Remote State Management
Use AWS S3 for storing Terraform state:
```hcl
terraform {
  backend "s3" {
    bucket         = "my-terraform-state"
    key            = "state/terraform.tfstate"
    region         = "us-east-1"
  }
}
```
### 2. Terraform Modules
Organize reusable code:
```hcl
module "ec2" {
  source = "./modules/ec2"
  instance_type = "t2.micro"
}
```
### 3. Multiple Environments
Use workspaces:
```bash
terraform workspace new dev
terraform workspace select dev
```
### 4. Best Practices
Version control state files.
Use .tfvars for sensitive data (never commit it to Git).
Implement linting tools like tflint.

## 🧹 Clean Up
To destroy all resources:
```bash
terraform destroy
```

## 📚 Resources
Terraform Documentation
AWS CLI Documentation
Visual Studio Code

This repository is a complete Zero to Hero guide, covering basics to advanced Terraform concepts. Clone this repo and start your cloud journey today!

