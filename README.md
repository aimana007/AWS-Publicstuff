# AWS CloudFormation Infrastructure Template

A production-ready CloudFormation template for deploying a basic web application infrastructure on AWS. This template creates a VPC with public/private subnets, an EC2 web server, and an S3 bucket with proper security configurations.

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    VPC (10.0.0.0/16)                   │
│  ┌─────────────────────┐  ┌─────────────────────────────┐ │
│  │   Public Subnet     │  │    Private Subnet           │ │
│  │   (10.0.1.0/24)     │  │    (10.0.2.0/24)          │ │
│  │                     │  │                             │ │
│  │  ┌───────────────┐  │  │                             │ │
│  │  │  EC2 Instance │  │  │     (Future resources)      │ │
│  │  │  Web Server   │  │  │                             │ │
│  │  └───────────────┘  │  │                             │ │
│  └─────────────────────┘  └─────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
                          │
                    ┌───────────┐
                    │ S3 Bucket │
                    └───────────┘
```

## Features

- **VPC Infrastructure**: Isolated network with public and private subnets across multiple AZs
- **Security Groups**: Preconfigured firewall rules for web traffic (HTTP/HTTPS) and SSH access
- **EC2 Web Server**: Amazon Linux 2 instance with Apache automatically installed
- **S3 Storage**: Encrypted bucket with versioning and public access blocked
- **IAM Roles**: Secure permissions for EC2 to access S3 resources
- **Parameterized**: Easy customization for different environments (dev/staging/prod)

## Prerequisites

Before deploying this template, ensure you have:

1. **AWS CLI** installed and configured with appropriate permissions
2. **EC2 Key Pair** created in your target AWS region for SSH access
3. **IAM permissions** to create VPC, EC2, S3, and IAM resources
