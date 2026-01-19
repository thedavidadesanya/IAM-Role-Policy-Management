# Architecture Overview – IAM Role & Policy Management
<img width="355" height="571" alt="Architecure drawio" src="https://github.com/user-attachments/assets/ddbdcd43-c777-4920-9ae8-d733af1f1f36" />

*Figure 1: IAM role-based access architecture enforcing least-privilege access from EC2 to S3.*

## Objective
The objective of this architecture is to securely grant an EC2 instance
read-only access to a specific Amazon S3 bucket using AWS Identity and Access
Management (IAM) roles and policies, while enforcing the principle of least
privilege.

No long-term credentials are stored on the EC2 instance.

---

## High-Level Architecture
As shown in Figure 1, an IAM role with a custom read-only policy is attached to
an EC2 instance, allowing secure, scoped access to a specific S3 bucket without
the use of long-term credentials.


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
