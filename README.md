# Terraform AWS Infrastructure Project

This Terraform project sets up the infrastructure for an AWS environment, including a backend for managing Terraform state. The project includes an EC2 instance, an S3 bucket, and utilizes a module named `app-module` to streamline the configurations.

## Table of Contents
- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Setting Up Terraform Backend](#setting-up-terraform-backend)
- [Building the Infrastructure](#building-the-infrastructure)
- [Terraform Modules](#terraform-modules)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The project creates an AWS infrastructure with the following components:

- An EC2 instance
- An S3 bucket
- Terraform backend utilizing an S3 bucket and DynamoDB table for locking

## Prerequisites

Ensure you have the following prerequisites before running Terraform:

- [Terraform](https://www.terraform.io/downloads.html) installed on your machine
- AWS CLI configured with the necessary credentials

## Setting Up Terraform Backend

1. Create an S3 bucket to serve as the backend for Terraform state.
2. Uncomment the following code in `tf-backend/main.tf` after creating the S3 bucket:

```hcl
# backend "s3" {
#   bucket         = "your-s3-bucket-name"
#   key            = "tf-backend/terraform.tfstate"
#   region         = "your-region"
#   encrypt        = true
#   dynamodb_table = "tf-locking"
# }
```

Replace `"your-s3-bucket-name"` and `"your-region"` with the appropriate values.

3. Bootstrap the Terraform backend by running the following commands in the `tf-backend` directory:

```bash
terraform init
terraform apply
```

## Building the Infrastructure

1. In the root directory, run the following commands to initialize and apply the Terraform configurations:

```bash
terraform init
terraform apply
```

2. Review the changes and confirm by entering `yes` when prompted.

## Terraform Modules

This project uses a module named `app-module` to organize and manage specific configurations. The module is located in the `modules` directory.
