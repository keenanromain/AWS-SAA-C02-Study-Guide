# AWS-SAA-C02-Study-Guide

## Table of Contents
<a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#introduction">Introduction</a>
<a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#identity-access-management-iam"> Identity Access Management (IAM)</a>

## Introduction

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

  5. <a href="https://aws.amazon.com/ec2/autoscaling/faqs/"> Amazon EC2 Auto Scaling FAQs </a>

  6. <a href="https://aws.amazon.com/ebs/faqs/">Amazon EBS FAQs</a>

  7. <a href="https://aws.amazon.com/s3/faqs/">Amazon S3 FAQs</a>

  8. <a href="https://aws.amazon.com/route53/faqs/"> Amazon Route 53 FAQs</a>

  9. <a href="https://aws.amazon.com/elasticloadbalancing/faqs/"> Elastic Load Balancing FAQs</a>

  10. <a href="https://aws.amazon.com/api-gateway/faqs/"> AWS API Gateway FAQs</a>

  11. <a href="https://aws.amazon.com/storagegateway/faqs/"> AWS Storage Gateway FAQs</a>

  12. <a href="https://aws.amazon.com/efs/faq/"> Amazon EFS FAQs</a>

  13. <a href="https://aws.amazon.com/fsx/windows/faqs/">Amazon FSx for Windows File Server FAQs</a>

  14. <a href="https://aws.amazon.com/fsx/lustre/faqs/">Amazon FSx for Lustre FAQs</a>

## Identity Access Management (IAM)

### IAM's Key Features:

IAM offers a centralized hub of control within AWS & is a focal point that integrates with all other AWS Services.
IAM comes with the ability to share access at granular levels of permission and it supports the ability to use identity federation (the process of delegating authentication responsibility to a trusted external party like Facebook or Google) for temporary or limited access. IAM comes with MFA support and allows you to set up custom password rotation policy across your entire organiation. It is also PCI DSS compliant (passes government mandated credit card security regulations).

### Entities within IAM:

**Users** - any individual end user such as an employee, system architect, CTO, etc.

**Groups** - any collection of similar people with shared permissions such as system administrators, HR employees, finance teams, etc. Each user within their specified group will inherit the permissions set for the group.

**Roles** - any software service that needs to be granted permissions to do its job, e.g- AWS Lambda needing write permissions to S3 or a fleet of EC2 instances needing read permissions from a RDS MySQL database.

**Policies** - the documented rulesets that are applied to grant or limit access. In order for users, groups, or roles to properly set permissions, they use policies. Policies are written in JSON and you can either use custom policies for your specific needs or use the default policies set by AWS.

![Screen Shot 2020-06-06 at 10 49 48 PM](https://user-images.githubusercontent.com/13093517/83959193-11533980-a848-11ea-9d03-d8133e0aaa86.png)

IAM Policies are separated from the other entities above because they are not an IAM Identity. Instead, they are attached to IAM Identities so that the IAM Identity in question can perform its neccessary function.

### IAM Details:

- IAM is a global AWS services that is not limited by regions. Any user, group, role or policy is accessible globally.

- The root account with complete admin access is the account used to sign up for AWS. Therefore, the email address used to create the AWS account for use should probably be the official company email address.

- New users have *NO* permissions when their accounts are first created. This is a secure way of delegating access as permissions must be intentionally granted.

- When joining the AWS ecosystem for the first time, new users are supplied an access key ID and a secret access key ID. These are created just once specifically for the new user to join, so if they are lost simply generate a new pair of access key IDs and secret access key IDs.

- When creating your AWS account, you may have an existing identity provider internal to your company that offers Single Sign On (SSO). If this is the case, it is useful, efficient, and entirely possible to reuse your existing identities on AWS. To do this, you let an IAM role be assumed by one of the Active Directories as the IAM ID Federation feature allows an external service the ability to assume an IAM role.

- IAM Roles can be assigned to a service, such as an EC2 instance, prior to its first use or creation or after its been in used/created. You can change permissions multiple times. This can all be done by using both the AWS console & AWS command line tools.

- You cannot nest IAM Groups. Individual IAM users can belong to multiple groups, but creating subgroups so that one IAM Group is embedded inside of another IAM Group is not possible.

- With IAM Policies, you can easily add tags that help define which resources are accessible by whom. These tags are then used to control access via a particular IAM policy. For example, production and development EC2 instances might be tagged as such. This would ensure that people who should only be able to access development instances cannot access production instances.  

### Priority Levels in IAM:
- **Explicit Deny**: Denies access to a particular resource and this ruling cannot be overruled.

- **Explicit Allow**: Allows access to a particular resource so long as there is not an associated explicit deny.

- **Default Deny (or Implicit Deny)**: IAM identities start off with no resource access. Access instead must be granted.


## Simple Storage Service (S3)

### S3's Key Features:
S3 provides developers and IT teams with secure, durable, and highly-scalable object storage. Object storage, as opposed to block storage, is a general term that refers to data composed of three things:

  1.) the data itself that you want to store

  2.) an expandable amount of metadata

  3.) a unique identifier so that the data can be retrieved 

This makes it a perfect candidate to host files or directories and a poor candidate to host databases or operating systems. The following table highlights key differences between object and block storage:

![Screen Shot 2020-06-05 at 3 34 57 PM](https://user-images.githubusercontent.com/13093517/83915925-352c5780-a742-11ea-975b-53d4e5d07e7c.png)


Data uploaded into S3 is spread across multiple files and facilities. The files uploaded into S3 have an upper-bound of 5TB per file and the number of files that can be uploaded is virtually limitless. S3 buckets, which contain all files, are named in a universal namespace so uniqueness is required. All successful uploads will return an HTTP 200 response.

### S3 Key Details:
- Objects (regular files or directories) are stored in S3 with a key, value, version ID, and metadata. They can also contain subresources for access control lists which are basically permissions for the object itself or they can contain torrents.
- The data consistency model for S3 ensures immediate read access for new objects after the initial PUT requests. These new objects are introduced into AWS for the first time and thus do not need to be updated anywhere so they are available immediately.
- The data consistency model for S3 ensures eventual read consistency for PUTS and DELETES of already existing objects. This is because the change takes a little time to propagate across the entire Amazon network.

- Because of the eventual consistency model when updating existing objects in S3, those updates might not be immediately reflected. As object updates are made to the same key, an older version of the object might be provided back to the user when the next read request is made. 

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
- S3 presigned URLs provide temporary access (upload or download) to an object. They are commonly used to provide access to private objects. You can specify the duration of the URL's existence.
- When you upload new files, they will not inherit the properties of the previous version. 

### S3 Storage Classes:
**S3 Standard** - 99.99% availability and 11 x 9s durability. Stored redundantly across multiple devices in multiple facilities and is designed to withstand the failure of 2 concurrent data centers.

**S3 Infrequently Accessed (IA)** - For data that is needed less often, but when it is needed the data should be available quickly. Storage fee is cheaper, but charged for retrieval.

**S3 One Zone Infrequently Accessed (or RRS / Reduced Redundancy Storage)** -  For when you want the lower costs of IA, but do not require high availability. This is even cheaper because of it.

**S3 Intelligent Tiering** - Uses built-in ML/AI to determine the most cost-effective storage class and then automatically moves your data to the appropriate tier. It does this without operational overhead or performance impact.

**S3 Glacier** - low-cost storage class for data archiving. This class is for pure storage purposes where retrieval isn’t needed often at all. Retrieval times range from minutes to hours. There are differing retrieval methods depending on how acceptable the default retrieval times are for you:

    Expedited: 1 - 5 minutes, but this option is the most expensive
    Standard: 3 - 5 hours to restore.
    Bulk: 5 - 12 hours. This option has the lowest cost and is good for a large set of data.


**S3 Deep Glacier** - The lowest cost S3 storage where retrieval can take 12 hours.

<img width="1246" alt="storage_types" src="https://user-images.githubusercontent.com/13093517/83919060-e1247180-a747-11ea-9336-e92ee163ac7a.png">

### S3 Encryption:
S3 data can be encrypted both in transit and at rest.

**Encryption In Transit**: When the traffic passing between one endpoint to another is indecipherable. Anyone eavesdropping between server A and server B won’t be able to make sense of the information passing by. Encryption in transit for S3 is always achieved by SSL/TLS.

**Encryption At Rest**: When the immobile data sitting inside S3 is encrypted. If someone breaks into a server, they still won’t be able to access encrypted info within that server. Encryption at rest can be done either on the server-side or the client-side. The server-side is when S3 encrypts your data as it is being written to disk and decrypts it when you access it. The client-side is when you personally encrypt the object on your own and then upload it into S3 afterwards.

You can encrypted on the AWS supported server-side in the following ways:
- **S3 Managed Keys / SSE - S3 (server side encryption S3 )** - when Amazon manages the encryption and decryption keys for you automatically. In this scenario, you concede a little control to Amazon in exchange for ease of use.
- **AWS Key Management Service / SSE - KMS** - when Amazon and you both manage the encryption and decryption keys together.
- **Server Side Encryption w/ customer provided keys / SSE - C** - when I give Amazon my own keys that I manage. In this scenario, you concede ease of use in exchange for more control.

### S3 Versioning:
- When versioning is enabled, S3 stores all versions of an object including all writes and even deletes.
- It is a great feature for implictly backuping content and easy rollbacks in case of human error.
- It can be thought of as analogous to Git
- Once versioning is enabled on a bucket, it cannot be disabled - only suspended
- Versioning integrates w/ lifecycle rules so you can set rules to expire or migrate data based on their version
- Versioning also has MFA delete capability to provide an additional layer of security

### S3 Lifecycle Management:
- Automates the moving of objects between the different storage tiers
- Can be used in conjunction with versioning
- Lifecycle rules can be applied to both current and previous versions of an object

### S3 Cross Region Replication:
- Cross region replication only work if versioning is enabled
- When cross region replication is enabled, no pre-existing data is transferred. Only new uploads into the original bucket are replicated. All subsequent updates are replicated.
- When you replicate the contents of one bucket to another, you can actually change the ownership of the content if you want. You can also change the storage tier of the new bucket with the replicated content.
- When files are deleted in the original bucket (via a delete marker as versioning prevents true deletions), those deletes are not replicated
- <a href="https://aws.amazon.com/solutions/cross-region-replication-monitor/">Cross Region Replication Overview</a>
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-what-is-isnot-replicated.html#replication-what-is-not-replicated ">What is and isn’t replicated such as encrypted objects, deletes, items in glacier, etc.</a>

### S3 Transfer Acceleration:
- Transfer acceleration makes use of the CloudFront network by sending or receiving data at CDN points of presence (called edge locations) rather than slower uploads or downloads at the origin
- This is accomplished by uploading to a distinct URL for the edge location instead of the bucket itself. This is then transferred over the AWS network backbone at a much faster speed.
- <a href="https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html">You can test transfer acceleration speed directly in comparison to regular uploads</a>

### S3 Event Notications:
The Amazon S3 notification feature enables you to receive and send notifications when certain events happen in your bucket. To enable notifications, you must first configure the events you want Amazon S3 to publish (new object added, old object deleted, etc.) and the destinations where you want Amazon S3 to send the event notifications. Amazon S3 supports the following destinations where it can publish events:
- **Amazon Simple Notification Service (Amazon SNS)** - A web service that coordinates and manages the delivery or sending of messages to subscribing endpoints or clients.
- **Amazon Simple Queue Service (Amazon SQS)** - SQS offers reliable and scalable hosted queues for storing messages as they travel between computers.
- **AWS Lambda** - AWS Lambda is a compute service where you can upload your code and the service can run the code on your behalf using the AWS infrastructure. You package up and upload your custom code to AWS Lambda when you create a Lambda function. The S3 event triggering the Lambda function also can serve as the code's input.

###  S3 and ElasticSearch
- If you are using S3 to store log files, ElasticSearch provides full search capabilities for logs and can be used to search through data stored in an S3 bucket.
- You can integrate your ElasticSearch domain with S3 and Lambda. In this setup, any new logs received by S3 will trigger an event notification to Lambda, which in turn will then run your application code on the new log data. After your code finishes processing, the data will be streamed into your ElasticSearch domain and be available for observation.

### Maximizing S3 Read/Write Performance:
- If the request rate for reading and writing objects to S3 is extremely high, then you can use hash keys or random strings to prefix the object's name. In such cases, the partitions used to store the objects will be better distributed and therefore will allow better read/write performance on your objects. 
- If your S3 data is receiving a high number of GET requests from users, you should consider using Amazon CloudFront for performance optimization. By integrating CloudFront with S3, you can distribute content via CloudFront's cache to your users for lower latency and a higher data transfer rate. This also has the added bonus of sending fewer direct requests to S3 which will reduce costs. For example, suppose that you have a few objects that are very popular. CloudFront fetches those objects from S3 and caches them. CloudFront can then serve future requests for the objects from its cache, reducing the total number of GET requests it sends to Amazon S3.
- <a href="https://docs.aws.amazon.com/AmazonS3/latest/dev/request-rate-perf-considerations.html "> More information on how to ensure high performance in S3</a>

### S3 Server Access Logging
- Server access logging provides detailed records for the requests that are made to a bucket. Server access logs are useful for many applications. For example, access log information can be useful in security and access audits. It can also help you learn about your customer base and understand your Amazon S3 bill. 
- By default, logging is disabled. When logging is enabled, logs are saved to a bucket in the same AWS Region as the source bucket. 
- Each access log record provides details about a single access request, such as the requester, bucket name, request time, request action, response status, and an error code, if relevant.
- It works in the following way:
   - S3 periodically collecting access log records of the bucket you want to monitor
   - S3 then consolidates those records into log files
   - S3 finally uploads the log files to your secondary monitoring bucket as log objects



## CloudFront

### CloudFront's Key Features
The AWS CDN service is called CloudFront. It serves up cached content and assets for the increased global performance of your application. The main components of CloudFront are the edge locations (cache endpoints), the origin (original source of truth to be cached such as an EC2 instance, an S3 bucket, an Elastic Load Balancer or a Route 53 config), and the distribution (the arrangement of edge locations from the origin or basically the network itself). <a href="https://aws.amazon.com/cloudfront/features/">More info on CloudFront's features</a>

### CloudFront Key Details
- When content is cached, it is done for a certain time limit called the Time To Live, or TTL, which is always in seconds
- If needed, CloudFront can serve up entire websites including dynamic, static, streaming and interactive content. 
- Requests are always routed and cached in the nearest edge location for the user, thus propagating the CDN nodes and guaranteeing best performance for future requests.
- There are two different types of distributions: 
  - **Web Distribution**: web sites, normal cached items, etc
  - **RTMP**: streaming content, adobe, etc
- Edge locations are *NOT* just read only. They can be written to which will then return the write value back to the origin.
- Cached content can be manually invalidated or cleared beyond the TTL, but this does incur a cost.
- You can invalidate the distribution of certain objects or entire directories so that content is loaded directly from the origin everytime. Invalidating content is also helpful when debugging if content pulled from the origin seems correct, but pulling that same content from an edge location seems incorrect.
- You can set up a failover for the origin by creating an origin group with two origins inside. One origin will act as the primary and the other as the secondary. CloudFront will automatically switch between the two when the primary origin fails.
- Amazon CloudFront delivers your content from each edge location and offers a Dedicated IP Custom SSL feature. SNI Custom SSL works with most modern browsers.
- If you run PCI or HIPAA-compliant workloads and need to log usage data, you can do the following:
    - Enable CloudFront access logs. 
    - Capture requests that are sent to the CloudFront API.

### CloudFront Signed URLs and Signed Cookies
- CloudFront signed URLs and signed cookies provide the same basic functionality: they allow you to control who can access your content. These features exist because many companies that distribute content via the internet want to restrict access to documents, business data, media streams, or content that is intended for selected users. As an example, users who have paid a fee should be able to access private content that users on the free tier shouldn't. 
- If you want to serve private content through CloudFront and you're trying to decide whether to use signed URLs or signed cookies, consider the following:
  - Use signed URLs for the following cases:
    - You want to use an RTMP distribution. Signed cookies aren't supported for RTMP distributions.
    - You want to restrict access to individual files, for example, an installation download for your application.
    - Your users are using a client (for example, a custom HTTP client) that doesn't support cookies.
  - Use signed cookies for the following cases:
    - You want to provide access to multiple restricted files. For example, all of the files for a video in HLS format or all of the files in the paid users' area of a website.
    - You don't want to change your current URLs.

