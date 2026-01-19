# Architecture Overview – IAM Role & Policy Management

## Objective
The objective of this architecture is to securely grant an EC2 instance
read-only access to a specific Amazon S3 bucket using AWS Identity and Access
Management (IAM) roles and policies, while enforcing the principle of least
privilege.

No long-term credentials are stored on the EC2 instance.

---

## High-Level Architecture

User (Admin)
   |
   v
AWS IAM
   |-- IAM User (management access)
   |-- IAM Policy (S3 Read-Only)
   |-- IAM Role (assumed by EC2)
   |
   v
Amazon EC2
   |
   v
Amazon S3 (Read-Only Access)

---

## Components

### 1. IAM User
- Used only for administrative and configuration tasks
- Does not provide direct access to S3 data
- Permissions are scoped to IAM management activities

**Security Rationale:**  
Separates human access from service-level permissions.

---

### 2. IAM Policy – S3 Read-Only
- Grants the following permissions:
  - `s3:ListBucket`
  - `s3:GetObject`
- Scope is limited to a single S3 bucket

**Example Permissions:**
```json
s3:ListBucket
s3:GetObject
