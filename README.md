# Terraform AWS Infrastructure Project

This Terraform project sets up the infrastructure for an AWS environment, including a backend for managing Terraform state. The project includes an EC2 instance, an S3 bucket, and utilizes a module named `app-module` to streamline the configurations.

## Table of Contents
- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Setting Up Terraform Backend](#setting-up-terraform-backend)
- [Building the Infrastructure](#building-the-infrastructure)

## Project Overview

The project creates an AWS infrastructure with the following components:

- An EC2 instance
- An S3 bucket
- Terraform backend utilizing an S3 bucket and DynamoDB table for locking

## Prerequisites

Ensure you have the following prerequisites before running Terraform:

- [Terraform](https://www.terraform.io/downloads.html) installed on your machine
- AWS CLI configured with the necessary credentials

Certainly! Based on your description, let me provide a concise set of instructions to complement the existing readme file:

---

## Setting Up Terraform Backend

1. **Build Terraform Backend S3**:
   - Navigate to the `tf-backend` directory.
   - Run the following commands to initialize and apply, building the S3 bucket for Terraform backend:

     ```bash
     terraform init
     terraform plan
     terraform apply
     ```

2. **Uncomment Backend Configuration**:
   - After creating the S3 bucket, uncomment the backend configuration in `tf-backend/main.tf`.
   - Replace `"your-s3-bucket-name"` and `"your-region"` with appropriate values.

     ```hcl
     backend "s3" {
       bucket         = "your-s3-bucket-name"
       key            = "tf-backend/terraform.tfstate"
       region         = "your-region"
       encrypt        = true
       dynamodb_table = "tf-locking"
     }
     ```

3. **Bootstrap Terraform Backend**:
   - Run the following commands in the `tf-backend` directory:

     ```bash
     terraform init
     terraform plan
     terraform apply
     ```

## Building the Infrastructure

1. **Initialize and Apply Configurations**:
   - In the app directory, run the following commands to initialize and apply Terraform configurations:

     ```bash
     terraform init
     terraform plan
     terraform apply
     ```

2. **Review and Confirm**:
   - Review the proposed changes and confirm by entering `yes` when prompted.

