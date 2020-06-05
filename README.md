# AWS-SAA-C02-Study-Guide

## Identity Access Management (IAM)

### IAM's Key Features:

Offers a centralized hub of control within AWS & is a focal point that integrates with all other AWS Services.
IAM comes with the ability to share access at granular levels of permission and it supports the ability to use identity federation (the process of delegating authentication responsibility to a trusted external party like Facebook or Google) for temporary or limited access. IAM comes with MFA support and allows you to set up custom password rotation policy across your entire organiation. It is also PCI DSS compliant (passes government mandated credit card security regulations).

### Entities within IAM:

**Users** - any individual end user such as an employee, system architect, CTO, etc.
**Groups** - any collection of similar people with shared permissions such as system administrators, HR employees, finance teams, etc. Each user within their specified group will inherit the permissions set for the group.
**Roles** - any software service that needs to be granted permissions to do its job, e.g- AWS Lambda needing write permissions to S3 or a fleet of EC2 instances needing read permissions from a RDS MySQL database.
**Policies** - the documented rulesets that are applied to grant or limit access. In order for users, groups, or roles to properly set permissions, they use policies. Policies are written in JSON and you can either use custom policies for your specific needs or use the default policies set by AWS.

### IAM Details:

- IAM is a global AWS services that is not limited by regions. Any user, group, role or policy is accessible globally.
- The root account with complete admin access is the account used to sign up for AWS. Therefore, the email address used to create the AWS account for use should probably be the official company email address.
- New users have *NO* permissions when their accounts are first created. This is a secure way of delegating access as permissions must be intentionally granted.
- When joining the AWS ecosystem for the first time, new users are supplied an access key ID and a secret access key ID. These are created just once specifically for the new user to join, so if they are lost simply generate a new pair of access key IDs and secret access key IDs.
- When creating your AWS account, you may have an existing identity provider internal to your company that offers Single Sign On (SSO). If this is the case, it is useful, efficient, and entirely possible to reuse your existing identities on AWS. To do this, you let an IAM role be assumed by one of the Active Directories as the IAM ID Federation feature allows an external service the ability to assume an IAM role.
- IAM Roles can be assigned to a service, such as an EC2 instance, prior to its first use or creation or after its been in used/created. You can change permissions multiple times. This can all be done by using both the AWS console & AWS command line tools.
- You cannot nest IAM Groups. Individual IAM users can belong to multiple groups, but creating subgroups so that one IAM Group is embedded inside of another IAM Group is not possible.

### Priority Levels in IAM:
**Explicit Deny**: Denies access to a particular resource and this ruling cannot be overruled.
**Explicit Allow**: Allows access to a particular resource so long as there is not an associated explicit deny.
**Default Deny (or Implicit Deny)**: IAM identities start off with no resource access.

