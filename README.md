# quantiva-devtest-infra
Automated Dev/Test infrastructure deployment using AWS CloudFormation
# Quantiva Dev/Test Infrastructure Deployment

This repository automates the provisioning of Dev/Test AWS infrastructure for Quantiva Labs using AWS CloudFormation.

---

## 🔧 Features

- VPC with Subnet, Internet Gateway, Route Table
- EC2 instance (Windows) with:
  - Security Group for HTTP, RDP, SSH
  - Attached EBS volumes (root + data)
  - Tags for environment and ownership
- S3 bucket with versioning and tags
- Parameterized input for EC2 KeyPair and instance type

---

## 📁 Files

| File          | Description                                |
|---------------|--------------------------------------------|
| `example.yaml` | Main CloudFormation template               |
| `commands.md`  | AWS CLI steps to deploy and manage stack  |
| `.gitignore`   | Ignores local/temporary files (optional)  |

---

## 🚀 Deployment Steps

``` bash

### 1. Validate Template
aws cloudformation validate-template --template-body file://example.yaml

### 2. create stack

aws cloudformation create-stack \
  --stack-name my-infra-stack \
  --template-body file://example.yaml \
  --parameters ParameterKey=KeyName,ParameterValue=cwinkp ParameterKey=InstanceType,ParameterValue=t2.micro \
  --capabilities CAPABILITY_NAMED_IAM \
  --region us-west-1

### 3. Describe Stack

aws cloudformation describe-stacks \
  --stack-name my-infra-stack \
  --region us-west-1

### 4. Update Stack

aws cloudformation update-stack \
  --stack-name my-infra-stack \
  --template-body file://example.yaml \
  --parameters ParameterKey=KeyName,ParameterValue=cwinkp ParameterKey=InstanceType,ParameterValue=t2.micro \
  --capabilities CAPABILITY_NAMED_IAM \
  --region us-west-1

### 5. Delete Stack

aws cloudformation delete-stack \
  --stack-name my-infra-stack \
  --region us-west-1
