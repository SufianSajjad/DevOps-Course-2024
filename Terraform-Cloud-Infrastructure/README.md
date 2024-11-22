# 🚀 Terraform - AWS Cloud Infrastructure

This repository contains a **Terraform** project that provisions an EC2 instance on AWS. It uses **Infrastructure as Code (IaC)** to automate the creation of cloud resources, making deployments repeatable and consistent.

---

## 🚀 What This Project Does
- Provisions an EC2 instance on AWS.
- Configures the instance using the AMI ID and instance type defined in the variables.
- Outputs the instance ID after deployment.

---

## 📋 Prerequisites
Before running this Terraform project, ensure you have the following:

1. **Terraform Installed**: [Download Terraform](https://developer.hashicorp.com/terraform/downloads).
2. **AWS CLI Installed and Configured**: Set up your AWS credentials with the following command:
   ```bash
   aws configure

## 💻 How to Use
Clone the repository and navigate to the project directory:
   ```bash
   git clone https://github.com/YourUsername/DevOps-Course-2024.git
   cd DevOps-Course-2024/Terraform-Cloud-Infrastructure

Initialize Terraform in the directory:
   ```bash
   terraform init

Validate the configuration:
   ```bash
   terraform validate

Plan the infrastructure changes:
   ```bash
   terraform plan

Apply the changes to provision resources:
   ```bash
   terraform apply

Confirm the output (Instance ID will be displayed):
   ```bash
   Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
   Outputs:
   instance_id = "i-xxxxxxxxxxxxxxxxx"

---

## 🧹 Clean Up
To destroy the created resources, run:
   ```bash
   terraform destroy

---

## 📖 Learning Goals
This project showcases:

- The use of Terraform to provision and manage cloud infrastructure.
- How to define reusable and configurable variables.
- Generating outputs for deployed resources.
- Managing infrastructure through IaC practices.

---

## 🛠️ Technologies Used
- Terraform: For provisioning and managing infrastructure.
- AWS: Cloud provider for provisioning EC2 instances.
