# IAM Notes

## IAM User
1. **AWS IAM (Identity and Access Management)**
2. AWS IAM user is a service provided by Amazon Web Services that allows you to manage access to AWS resources within your organization.
3. **User authentication**: IAM users can be used to authenticate users who need to access AWS resources or services.
4. **Resource access control**: IAM users can be assigned permissions to access specific AWS resources or services.
5. **Cost-effective**: IAM users can help you control costs by limiting access to resources and services only to those who need them.
6. **Security management**: IAM users can be used to manage security and compliance within your organization. You can set up policies and roles that define what actions are allowed or denied for specific users.
7. Each IAM User is associated with one and only one AWS ROOT account.

## IAM Policies
- Policies define permissions using JSON documents.
- **Types of IAM Policies:** 
  1. **AWS-Managed Policies** – Predefined by AWS (e.g., AdministratorAccess, ReadOnlyAccess).
  2. **Customer-Managed Policies** – Custom policies created by users.
  3. **Inline Policies** – Policies directly attached to a single IAM entity (user, group, or role).

## IAM Groups
- IAM Groups allow managing permissions for multiple users at once.
- Users inherit permissions from groups.
- **Best Practice**: Assign policies to groups instead of individual users.

**Example Groups:**
- AdminGroup (Full access)
- DevGroup (Limited access)
- ReadOnlyGroup (Only read permissions)

## IAM Roles
- IAM Roles allow AWS services or users to assume temporary permissions.
- Unlike IAM users, roles do not have long-term credentials.
- **Used for:**
  - AWS services like EC2, Lambda, and ECS.
  - Cross-account access.
  - Federated access (SSO, Active Directory).

### IAM Role Example Use Case
- **An EC2 instance needs to access S3:**
  - Create an IAM Role with S3 permissions.
  - Attach the role to the EC2 instance.
  - EC2 gets temporary credentials automatically.

## Common IAM Exam Scenarios

| Scenario                            | Solution                                              |
|-------------------------------------|-------------------------------------------------------|
| Secure AWS console login            | Enable MFA for IAM users                              |
| Application needs access to S3      | Use IAM Role for EC2 instead of Access Keys           |
| Restrict user to only EC2 actions   | Attach a custom policy allowing only `ec2:*`          |
| Grant developers access to EC2 but not billing | Use IAM Groups and Managed Policies      |
| Root user best practice             | Enable MFA, create IAM users, avoid daily use         |
| Troubleshoot access issues          | Check IAM Policy Simulator & CloudTrail logs          |