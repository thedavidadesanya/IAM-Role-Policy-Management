# IAM-Role-Policy-Management
Using AWS IAM to secure AWS resources by defining permissions using IAM roles and policies. This project focuses on creating IAM users, roles, and policies to enforce least-privilege access, ensuring security and compliance.
# IAM Role & Policy Management on AWS

## Overview
This project demonstrates how to securely manage access to AWS resources using
IAM users, roles, and custom policies while enforcing the principle of least privilege.

The goal was to allow EC2 instances read-only access to a specific S3 bucket
without granting excessive permissions.

---

## Architecture
- IAM User for management access
- Custom IAM Policy with S3 read-only permissions
- IAM Role assumed by EC2
- EC2 instance accessing S3 via IAM role (no hardcoded credentials)

---

## Technologies Used
- AWS IAM
- Amazon EC2
- Amazon S3
- AWS CLI

---

## Implementation Steps
1. Created IAM user for administrative access
2. Defined a custom IAM policy granting limited S3 permissions
3. Created an IAM role with a trust relationship for EC2
4. Attached the role to an EC2 instance
5. Verified access using AWS CLI commands

---

## Security Best Practices Applied
- Principle of least privilege
- IAM roles instead of access keys on EC2
- Scoped S3 permissions
- Explicit deny by omission

---

## Verification
Allowed action:
```bash
aws s3 ls s3://example-bucket

---

## Blog Write-Up

A detailed walkthrough of this project, including design decisions,
security considerations, and lessons learned, is available on Medium:

👉 **How To Implement Least-Privilege IAM Access Using AWS Roles & Policies**  
https://medium.com/@davidace200/how-to-implement-least-privilege-iam-access-using-aws-roles-policies-c9ed8605d9da
