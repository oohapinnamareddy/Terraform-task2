# Terraform-task2
Task 2 (Terraform EC2)

👉 Create a file called README.md and copy-paste everything below.

# Task 2: EC2 Instance Creation Using Terraform

## Overview
This task demonstrates how to provision an AWS EC2 instance using **Terraform**.  
Terraform is used as an Infrastructure as Code (IaC) tool to automate EC2 creation instead of manual configuration.

---

## Prerequisites
- AWS Account
- IAM user with EC2 permissions
- AWS CLI configured or IAM role attached
- Terraform installed
- Key pair already created in AWS (`jenkins`)

---

## Terraform Files Used

### provider.tf
```hcl
provider "aws" {
  region = "us-east-1"
}


This file defines the AWS provider and region where resources will be created.

resource.tf
resource "aws_instance" "myinstance" {

  ami           = "ami-0532be01f26a3de55"
  instance_type = "t3.micro"
  key_name      = "jenkins"
  availability_zone = "us-east-1b"

  tags = {
    Name        = "FLM-Instance"
    Environment = "Dev"
    Client      = "Pearls"
  }
}


This file defines the EC2 instance configuration including:

AMI

Instance type

Key pair

Availability Zone

Resource tags

Terraform Commands Executed
terraform init
terraform plan
terraform apply


After confirmation, Terraform created the EC2 instance successfully.

Output

Terraform execution result:

aws_instance.myinstance: Creation complete after 13s
Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

Verification

EC2 instance is visible in AWS Console

Instance state: Running

Instance name: FLM-Instance

Region: us-east-1

Availability Zone: us-east-1b


Conclusion

This task demonstrates successful EC2 provisioning using Terraform, highlighting the benefits of Infrastructure as Code such as automation, consistency, and repeatability.
