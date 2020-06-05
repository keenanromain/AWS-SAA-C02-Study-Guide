# AWS-SAA-C02-Study-Guide

<a href="https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate-Exam-Guide_v1.1_2019_08_27_FINAL.pdf">**The official AWS Solutions Architect - Associate (SAA-C02) exam guide**</a>

**Exam Content Breakdown**:
![Screen Shot 2020-06-05 at 2 49 08 PM](https://user-images.githubusercontent.com/13093517/83912374-c2b87900-a73b-11ea-9691-b38383b43ff9.png)

*Domain 1: Design Resilient Architectures*

1.1 - Design a multi-tier architecture solution

1.2 - Design highly available and/or fault-tolerant architectures

1.3 - Design decoupling mechanisms using AWS services

1.4 - Choose appropriate resilient storage


*Domain 2: Design High-Performing Architectures*

2.1 - Identify elastic and scalable computesolutions for a workload

2.2 - Select high-performingand scalable storage solutions for a workload

2.3 - Select high-performingnetworking solutions for a workload

2.4 - Choose high-performingdatabase solutions for a workload


*Domain 3: Design Secure Applications and Architectures*

3.1 - Design secure access to AWS resources

3.2 - Design secure application tiers

3.3 - Select appropriate data security options


*Domain 4: Design Cost-Optimized Architectures*

4.1 - Identify cost-effective storage solutions

4.2 - Identify cost-effective compute and database services

4.3 - Design cost-optimized network architectures



## Required Reading:

1. <a href="https://d1.awsstatic.com/whitepapers/architecture/AWS_Well-Architected_Framework.pdf">AWS Well-Architected Framework</a>

2. <a href="https://aws.amazon.com/vpc/faqs/">Amazon VPC FAQs</a>

3. <a href="https://aws.amazon.com/autoscaling/faqs/"> AWS Autoscaling FAQs</a>

4. <a href="https://aws.amazon.com/ec2/faqs/">Amazon EC2 FAQs</a>

5. <a href="https://aws.amazon.com/ebs/faqs/">Amazon EBS FAQs</a>

6. <a href="https://aws.amazon.com/s3/faqs/">Amazon S3 FAQs</a>

7. <a href="https://aws.amazon.com/route53/faqs/"> Amazon Route 53 FAQs</a>

8. <a href="https://aws.amazon.com/elasticloadbalancing/faqs/"> Elastic Load Balancing FAQs</a>

9. <a href="https://aws.amazon.com/api-gateway/faqs/"> AWS API Gateway FAQs</a>

10. <a href="https://aws.amazon.com/storagegateway/faqs/"> AWS Storage Gateway FAQs</a>


## Identity Access Management (IAM)

### IAM's Key Features:

IAM offers a centralized hub of control within AWS & is a focal point that integrates with all other AWS Services.
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


## Simple Storage Service (S3)

### S3's Key Features:
S3 provides developers and IT teams with secure, durable, and highly-scalable object storage. Object storage, as opposed to block storage, is a general term that refers to data composed of three things: the data itself that you want to store, an expandable amount of metadata, and a unique identifier so that the data can be retrieved. This makes it a perfect candidate to host files or directories and a poor candidate to host databases or operating systems. The following table highlights key differences between object and block storage:

![Screen Shot 2020-06-05 at 3 34 57 PM](https://user-images.githubusercontent.com/13093517/83915925-352c5780-a742-11ea-975b-53d4e5d07e7c.png)


Data uploaded into S3 is spread across multiple files and facilities. The files uploaded into S3 have an upper-bound of 5TB per file and the number of files that can be uploaded is virtually limitless. S3 buckets, which contain all files, are named in a universal namespace so uniqueness is required. All successful uploads will return an HTTP 200 response.

### S3 Key Details:
- Objects (regular files or directories) are stored in S3 with a key, value, version ID, and metadata. They can also contain subresources for access control lists which are basically permissions for the object itself or they can contain torrents.
- The data consistency model for S3 ensures immediate read access for new objects after the initial PUT requests. These new objects are introduced into AWS for the first time and thus do not need to be updated anywhere so they are available immediately.
- The data consistency model for S3 ensures eventual read consistency for PUTS and DELETES of already existing objects. This is because the change takes a little time to propagate across the entire Amazon network.
- Amazon guarantees 99.999999999% (or 11 9s) durability for S3 data and comes with the following main features: 
1.) tiered storage and pricing variability
2.) lifecycle management to expire older content
3.) versioning for version control
4.) encryption for privacy
5.) MFA deletes to prevent accidental or malicious removal of content
6.) access control lists & bucket policies to secure the data
- S3 charges by:
1.) storage size
2.) number of requests
3.) storage management pricing (known as tiers)
4.) data transfer pricing (objects leaving/entering AWS via the internet)
5.) transfer acceleration (an optional speed increase for moving objects via Cloudfront)
6.) cross region replication (more HA than offered by default
- Bucket policies secure data at the bucket level while access control lists secure data at the more granular object level.
- By default, all newly created buckets are private.
- S3 can be configured to create access logs which can be shipped into another bucket in the current account or even a separate account all together. This makes it easy to monitor who accesses what inside S3.
- There are 3 different ways to share S3 buckets across accounts:
1.) For programmatic access only, use IAM & Bucket Policies to share entire buckets
2.) For programmatic access only, use ACLs & Bucket Policies to share objects
3.) For access via the console & the terminal, use cross-account IAM roles
- S3 is a great candidate for static website hosting. When you enable static website hosting for S3 you need both an index.html file and an error.html file. Static website hosting creates a website endpoint that can be accessed via the internet.

## S3 Storage Classes:
**S3 Standard** - 99.99% availability and 11 x 9s durability. Stored redundantly across multiple devices in multiple facilities and is designed to withstand the failure of 2 concurrent data centers.

**S3 Infrequently Accessed (IA)** - For data that is needed less often, but when it is needed the data should be available quickly. Storage fee is cheaper, but charged for retrieval.

**S3 One Zone Infrequently Accessed (or RRS / Reduced Redundancy Storage)** -  For when you want the lower costs of IA, but do not require high availability. This is even cheaper because of it.

**S3 Intelligent Tiering** - Uses built-in ML/AI to determine the most cost-effective storage class and then automatically moves your data to the appropriate tier. It does this without operational overhead or performance impact.

**S3 Glacier** - low-cost storage class for data archiving. This class is for pure storage purposes where retrieval isn’t needed often at all. Retrieval times range from minutes to hours. There is an expedited feature however, if the feature's extra cost is worth the time-performance improvement.

**S3 Deep Glacier** - The lowest cost S3 storage where retrieval can take 12 hours.

