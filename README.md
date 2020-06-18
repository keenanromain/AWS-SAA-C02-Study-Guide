# AWS-SAA-C02-Study-Guide

## Table of Contents
1. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#introduction">Introduction</a>

2. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#identity-access-management-iam">Identity Access Management (IAM)</a>

3. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#simple-storage-service-s3">Simple Storage Service (S3)</a>

4. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#cloudfront">CloudFront</a>

5. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#snowball">Snowball</a>

6. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#storage-gateway">Storage Gateway</a>

7. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#elastic-compute-cloud-ec2">Elastic Compute Cloud (EC2)</a>

8. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#elastic-block-store-ebs">Elastic Block Store (EBS)</a>

9. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#elastic-network-interfaces-eni">Elastic Network Interfaces (ENI)</a>

10. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#security-groups">Security Groups</a>

11. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#web-application-firewall-waf">Web Application Firewall (WAF)</a>

12. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#cloudwatch">CloudWatch</a>

13. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#cloudtrail">CloudTrail</a>

14. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#elastic-file-system-efs">Elastic File System (EFS)</a>

15. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#amazon-fsx-for-windows">Amazon FSx for Windows</a>

16. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#amazon-fsx-for-lustre">Amazon FSx for Lustre</a>

17. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#relational-database-service-rds">Relational Database Service (RDS)</a>

18. <a href="https://github.com/keenanromain/AWS-SAA-C02-Study-Guide#aurora">Aurora</a>

## Introduction

<a href="https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate-Exam-Guide_v1.1_2019_08_27_FINAL.pdf">**The official AWS Solutions Architect - Associate (SAA-C02) exam guide**</a>

### Exam Content Breakdown
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



### Required Reading:

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

### IAM Simplified:

IAM offers a centralized hub of control within AWS & is a focal point that integrates with all other AWS Services.
IAM comes with the ability to share access at granular levels of permission and it supports the ability to use identity federation (the process of delegating authentication responsibility to a trusted external party like Facebook or Google) for temporary or limited access. IAM comes with MFA support and allows you to set up custom password rotation policy across your entire organiation. It is also PCI DSS compliant (passes government mandated credit card security regulations).

### Entities within IAM:

**Users** - any individual end user such as an employee, system architect, CTO, etc.

**Groups** - any collection of similar people with shared permissions such as system administrators, HR employees, finance teams, etc. Each user within their specified group will inherit the permissions set for the group.

**Roles** - any software service that needs to be granted permissions to do its job, e.g- AWS Lambda needing write permissions to S3 or a fleet of EC2 instances needing read permissions from a RDS MySQL database.

**Policies** - the documented rulesets that are applied to grant or limit access. In order for users, groups, or roles to properly set permissions, they use policies. Policies are written in JSON and you can either use custom policies for your specific needs or use the default policies set by AWS.

![Screen Shot 2020-06-06 at 10 49 48 PM](https://user-images.githubusercontent.com/13093517/83959193-11533980-a848-11ea-9d03-d8133e0aaa86.png)

IAM Policies are separated from the other entities above because they are not an IAM Identity. Instead, they are attached to IAM Identities so that the IAM Identity in question can perform its neccessary function.

### IAM Key Details:

- IAM is a global AWS services that is not limited by regions. Any user, group, role or policy is accessible globally.

- The root account with complete admin access is the account used to sign up for AWS. Therefore, the email address used to create the AWS account for use should probably be the official company email address.

- New users have *NO* permissions when their accounts are first created. This is a secure way of delegating access as permissions must be intentionally granted.

- When joining the AWS ecosystem for the first time, new users are supplied an access key ID and a secret access key ID when you grant them programmatic access. These are created just once specifically for the new user to join, so if they are lost simply generate a new pair of access key IDs and secret access key IDs. Access keys are only used for the AWS CLI and SDK so you cannot use them to access the console.

- When creating your AWS account, you may have an existing identity provider internal to your company that offers Single Sign On (SSO). If this is the case, it is useful, efficient, and entirely possible to reuse your existing identities on AWS. To do this, you let an IAM role be assumed by one of the Active Directories as the IAM ID Federation feature allows an external service the ability to assume an IAM role.

- IAM Roles can be assigned to a service, such as an EC2 instance, prior to its first use or creation or after its been in used/created. You can change permissions multiple times. This can all be done by using both the AWS console & AWS command line tools.

- You cannot nest IAM Groups. Individual IAM users can belong to multiple groups, but creating subgroups so that one IAM Group is embedded inside of another IAM Group is not possible.

- With IAM Policies, you can easily add tags that help define which resources are accessible by whom. These tags are then used to control access via a particular IAM policy. For example, production and development EC2 instances might be tagged as such. This would ensure that people who should only be able to access development instances cannot access production instances.  

### Priority Levels in IAM:
- **Explicit Deny**: Denies access to a particular resource and this ruling cannot be overruled.

- **Explicit Allow**: Allows access to a particular resource so long as there is not an associated explicit deny.

- **Default Deny (or Implicit Deny)**: IAM identities start off with no resource access. Access instead must be granted.


## Simple Storage Service (S3)

### S3 Simplified:
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
- Amazon guarantees 99.999999999% (or 11 9s) durability for all S3 storage classes except its Reduced Redundancy Storage class.
- S3 comes with the following main features:

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
- When you upload new files, they will not inherit the properties of the previous version. 

### S3 Storage Classes:
**S3 Standard** - 99.99% availability and 11 x 9s durability. Stored redundantly across multiple devices in multiple facilities and is designed to withstand the failure of 2 concurrent data centers.

**S3 Infrequently Accessed (IA)** - For data that is needed less often, but when it is needed the data should be available quickly. Storage fee is cheaper, but charged for retrieval.

**S3 One Zone Infrequently Accessed (an improvement of the legacy RRS / Reduced Redundancy Storage)** -  For when you want the lower costs of IA, but do not require high availability. This is even cheaper because of it.

**S3 Intelligent Tiering** - Uses built-in ML/AI to determine the most cost-effective storage class and then automatically moves your data to the appropriate tier. It does this without operational overhead or performance impact.

**S3 Glacier** - low-cost storage class for data archiving. This class is for pure storage purposes where retrieval isn’t needed often at all. Retrieval times range from minutes to hours. There are differing retrieval methods depending on how acceptable the default retrieval times are for you:

    Expedited: 1 - 5 minutes, but this option is the most expensive.
    Standard: 3 - 5 hours to restore.
    Bulk: 5 - 12 hours. This option has the lowest cost and is good for a large set of data.

The Expedited duration listed above could possibly be longer during rare situations of unusually high demand. If it is absolutely critical to have quick access to your Glacier data under all circumstances, you must purchase Provisioned Capacity. Provisioned Capacity guarentees that Expedited retrievals always work within the time constraints of 1 to 5 minutes.

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

### S3 Multipart Upload
- Multipart upload allows you to upload a single object as a set of parts. Each part is a contiguous portion of the object's data. You can upload these object parts independently and in any order. 
- If transmission of any part fails, you can retransmit that part without affecting other parts. After all parts of your object are uploaded, Amazon S3 assembles these parts and creates the object.
- Possible reasons for why you would want to use Multipart upload:
  - Multipart upload delivers the ability to begin an upload before you know the final object size.
  - Multipart upload delivers improved throughput.
  - Multipart upload delivers the ability to pause and resume object uploads.
  - Multipart upload delivers quick recovery from network issues.
- You can use an AWS SDK to upload an object in parts. Alternatively, you can perform the same action via the AWS CLI.

### S3 Pre-signed URLs
- All S3 objects are private by default, however the object owner of a private bucket with private objects can optionally share those objects with without having to change the permissions of the bucket to be public.
- This is done by creating a pre-signed URL. Using your own security credentials, you can grant time-limited permission to download or view your private S3 objects.
- When you create a pre-signed URL for your S3 object, you must do the following:
  - provide your security credentials
  - specify a bucket
  - specify an object key
  - specify the HTTP method (GET to download the object)
  - specift the expiration date and time.
  
- The pre-signed URLs are valid only for the specified duration and anyone who receives the pre-signed URL within that duration can then access the object.
- The following diagram highlights how Pre-signed URLs work:

![Screen Shot 2020-06-09 at 8 20 53 PM](https://user-images.githubusercontent.com/13093517/84213482-c6773300-aa8e-11ea-84a1-3c17e14197bc.png)


## CloudFront

### CloudFront Simplified
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
- An Origin Access Identity (OAI) is used for sharing private content via CloudFront. The OAI is a virtual user that will be used to give your CloudFront distribution permission to fetch a private object from your origin (e.g. S3 bucket).

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

## Snowball

### Snowball Simplified
Snowball is a giant physical disk that is used for migrating high quantities of data into AWS. It is a peta-byte scale data transport solution. Using a large disk like Snowball helps to circumvent common large scale data transfer problems such as high network costs, long transfer times, and security concerns. Snowballs are extremely secure by design and once the data transfer is complete, the snowballs are wiped clean of your data.

### Snowball Key Details
- Snowball is a strong choice for a data transfer job if you need a secure and quick data transfer ranging in the terabytes to many petabytes into AWS. 
- Snowball can also be the right choice if you don’t want to make expensive upgrades to your existing network infrastructure, if you frequently experience large backlogs of data, if you're located in a physically isolated environment, or if you're in an area where high-speed internet connections are not available or cost-prohibitive.
- As a rule of thumb, if it takes more than one week to upload your data to AWS using the spare capacity of your existing internet connection, then you should consider using Snowball. 
- For example, if you have a 100 Mb connection that you can solely dedicate to transferring your data and you need to transfer 100 TB of data in total, it will take more than 100 days for the transfer to complete over that connection. You can make the same transfer in about a week by using multiple Snowballs.
- Here is a reference for when Snowball should be considered based on the number of days it would take to make the same transfer over an internet connection:
![Screen Shot 2020-06-07 at 10 53 22 PM](https://user-images.githubusercontent.com/13093517/83988618-c271d680-a911-11ea-9594-a82f690a786b.png)

### Snowball Edge and Snowmobile
- Snowball Edge is a specific type of Snowball that comes with both compute *and* storage capabilities via AWS Lambda and specific EC2 instance types. This means you can run code within your snowball while your data is en route to an Amazon data center. This enables support of local workloads in remote or offline locations and as a result, Snowball Edge does not need to be limited to a data transfer service. An interesting use case is with airliners. Planes sometimes fly with snowball edges onboard so they can store large amounts of flight data and compute necessary functions for the plane’s own systems. Snowball Edges can also be clustered locally for even better performance.
- Snowmobile is an exabyte-scale data transfer solution. It is a data transport solution for 100 petabytes of data and is contained within a 45-foot shipping container hauled by a semi-truck. This massive transfer makes sense if you want to move your entire data center with years of data into the cloud.

## Storage Gateway

### Storage Gateway Simplified
Storage Gateway is a service that connects on-premise environments with cloud-based storage in order to seamlessly and securely integrate an on-prem application with a cloud storage backend. and Volume Gateway as a way of storing virtual hard disk drives in the cloud. 


### Storage Gateway Key Details
- The Storage Gateway service can either be a physical device or a VM image downloaded onto a host in an on-prem data center. It acts as a bridge to send or receive data from AWS.
- Storage Gateway can sit on top of VMWare's ESXi hypervisor for Linux machines and Microsoft’s Hyper-V hypervisor for Windows machines.
- The three types of Storage Gateways are below:
  - **File Gateway** - Operates via NFS or SMB and is used to store files in S3 over a network filesystem mount point in the supplied virtual machine. Simply put, you can think of a File Gateway as a file system mount on S3.
  - **Volume Gateway** - Operates via iSCSI and is used to store copies of hard disk drives or virtual hard disk drives in S3. These can be achieved via *Stored Volumes* or *Cached Volumes*. Simply put, you can think of Volume Gateway as a way of storing virtual hard disk drives in the cloud. 
  - **Tape Gateway** - Operates as a Virtual Tape Library
- Relevant file information passing through Storage Gateway like file ownership, permissions, timestamps, etc. are stored as metadata for the objects that they belong to. Once these file details are stored in S3, they can be managed natively. This mean all S3 features like versioning, lifecycle management, bucket policies, cross region replication, etc. can be applied as a part of Storage Gateway.
- Applications interfacing with AWS over the Volume Gateway is done over the iSCSI block protocol. Data written to these volumes can be asynchronously backed up into AWS Elastic Block Store (EBS) as point-in-time snapshots of the volumes’ content. These kind of snapshots act as incremental backups that capture only changed state similar to a pull request in Git. Further, all snapshots are compressed to reduce storage costs.
- Tape Gateway offers a durable, cost-effective way of archiving and replicating data into S3 while getting rid of tapes (old-school data storage). The Virtual Tape Library, or VTL, leverages existing tape-based backup infrastructure to store data on virtual tape cartridges that you create on the Tape Gateway. It’s a great way to modernize and move backups into the cloud.

### Volume Gateway: Stored Volumes vs. Cached Volumes
- Volume Gateway's **Stored Volumes** let you store data locally on-prem and backs the data up to AWS as a secondary data source. Stored Volumes allow low-latency access to entire datasets, while providing high availability over a hybrid cloud solution. Further, you can mount Stored Volumes on application infrastructure as iSCSI drives so when data is written to these volumes, the data is both written onto the on-prem hardware and asynchronously backed up as snapshots in AWS EBS or S3.
  - In the following diagram of a Stored Volume architecture, data is served to the user from the Storage Area Network, Network Attached, or Direct Attached Storage within your data center. S3 exists just as a secure and reliable backup.
  - ![Screen Shot 2020-06-08 at 5 10 33 PM](https://user-images.githubusercontent.com/13093517/84080932-05cc5380-a9ab-11ea-8dd5-a80717b1b067.png)

- Volume Gateway's **Cached Volumes** differ as they do not store the entire dataset locally like Stored Volumes. Instead, AWS is used as the primary datasource and the local hardware is used as a caching layer. Only the most frequently used components are retained onto the on-prem infrastructure while the remaining data is served from AWS. This minimizes the need to scale on-prem infrastructure while still maintaining low-latency access to the most referenced data.
  - In the following diagram of a Cached Volume architecture, the most frequently accessed data is served to the user from the Storage Area Network, Network Attached, or Direct Attached Storage within your data center. S3 serves the rest of the data from AWS.
  - ![Screen Shot 2020-06-08 at 5 17 02 PM](https://user-images.githubusercontent.com/13093517/84081406-e5e95f80-a9ab-11ea-82d2-8bd1a53876ba.png)


## Elastic Compute Cloud (EC2)

### EC2 Simplified
EC2 spins up resizeable server instances that can scale up and down quickly. An instance is a virtual server in the cloud. With Amazon EC2, you can set up and configure the operating system and applications that run on your instance. Its configuration at launch is a live copy of the *Application Machine Image (AMI)* that you specify when you launched the instance. EC2 has an extremely reduced timeframe for provisioning and booting new instances and EC2 ensures that you pay as you go, pay for what you use, pay less as you use more, and pay even less when you reserve capacity. When your EC2 instance is running, you are charged on CPU, memory, storage, and networking. When it is stopped, you are only charged for EBS storage.

### EC2 Key Details
- You can launch different types of instances from a single AMI. An instance type essentially determines the hardware of the host computer used for your instance. Each instance type offers different compute and memory capabilities. You should select an instance type based on the amount of memory and computing power that you need for the application or software that you plan to run on top of the instance.   
- You can launch multiple instances of an AMI, as shown in the following figure:

![architecture_ami_instance](https://user-images.githubusercontent.com/13093517/84097031-64a4c380-a9d1-11ea-8358-1c3eec1c4471.png)

- You have the option of using dedicated tenancy with your instance. This means that within an AWS datacenter, you have exclusive access to physical hardware. Naturally, this option incurs a high cost, but it makes sense if you work with technology that has a strict licensing policy. 
- With EC2 VM Import, you can import existing VMs into AWS as long as those hosts use VMware ESX, VMware Workstation, Microsoft Hyper-V, or Citrix Xen virtualization formats.
- When you launch a new EC2 instance, EC2 attempts to place the instance in such a way that all of your VMs are spread out across different hardware to limit failure to a single location. You can use placement groups to influence the placement of a group of interdependent instances that meet the needs of your workload. There is an explanation about placement groups in a section below.
- When you launch an instance in Amazon EC2, you have the option of passing user data to the instance when the instance starts. This user data can be used to run common automated configuration tasks or scripts. For example, you can pass a bash script that ensures htop is installed on the new EC2 host and is always active.
- By default, the public IP address of an EC2 Instance is released when the instance is stopped even if its stopped temporarily. Therefore, it is best to refer to an instance by its external DNS hostname. If you require a persistent public IP address that can be associated to the same instance, use an Elastic IP address which is basically a static IP address instead. 
- If you have requirements to self-manage a SQL database, EC2 can be a solid alternative to RDS. To ensure high availability, remember to have at least one other EC2 Instance in a separate Availability zone so even if a DB instance goes down, the other(s) will still be available.
- A golden image is simply an AMI that you have fully customized to your liking with all necessary software/data/configuration details set and ready to go once. This personal AMI can then be the source from which you launch new instances.
- Instance status checks check the health of the running EC2 server, systems status check monitor the health of the underlying hypervisor. If you ever notice a systems status issue, just stop the instance and start it again (no need to reboot) as the VM will start up again on a new hypervisor.

### EC2 Instance Pricing
- **On-Demand instances** are based on a fixed rate by the hour or second. As the name implies, you can start an On-Demand instance whenever you need one and can stop it when you no longer need it. There is no requirement for a long-term commitment.
- **Reserved instances** ensure that you keep exclusive use of an instance on 1 or 3 year contract terms. The long-term commitment provides significantly reduced discounts at the hourly rate. 
- **Spot instances** take advantage of Amazon’s excess capacity and work in an interesting manner. In order to use them, you must financially bid for access. Because Spot instances are only available when Amazon has excess capacity, this option makes sense only if your app has flexible start and end times. You won’t be charged if your instance stops due to a price change (e.g., someone else just bid a higher price for the access) and so consequently your workload doesn’t complete. However, if you terminate the instance yourself you will be charged for any hour the instance ran. Spot instances are normally used in batch processing jobs. 

### Reserved Instances: Standard Reserved vs. Convertible Reserved vs. Scheduled Reserved
- **Standard Reserved Instances** have inflexible reservations that are discounted at 75% off of On-Demand instances. Standard Reserved Instances cannot be moved between regions. You can choose if a Reserved Instance applies to either a specific Availability Zone, or an Entire Region, but you cannot change the region.
- **Convertible Reserved Instances** are instances that are discounted at 54% off of On-Demand instances, but you can also modify the instance type at any point. For example, you suspect that after a few months your VM might need to change from general purpose to memory optimized, but you aren't sure just yet. So if you think that in the future you might need to change your VM type or upgrade your VMs capacity, choose Convertible Reserved Instances. There is no downgrading instance type with this option though.
- **Scheduled Reserved Instances** are reserved according to a specified timeline that you set. For example, you might use Scheduled Reserved Instances if you run education software that only needs to be available during school hours. This option allows you to better match your needed capacity with a recurring schedule so that you can save money.


### EC2 Instance Lifecycle
The following table highlights the many instance states that a VM can be in at a given time. 

| Instance state | Description | Billing |
| ------------- | ------------- |--------------|
| `pending` | The instance is preparing to enter the `running` state. An instance enters the pending state when it launches for the first time, or when it is started after being in the `stopped` state.   | Not billed
| `running`  | The instance is running and ready for use.  | Billed |
| `stopping`  | The instance is preparing to be stopped or stop-hibernated.  | Not billed if preparing to stop. Billed if preparing to hibernate |
| `stopped` | The instance is shut down and cannot be used. The instance can be started at any time. | Not billed |
| `shutting-down`  | The instance is preparing to be terminated.  | Not billed |
| `terminated`  | The instance has been permanently deleted and cannot be started.  | Not billed |

**Note**: Reserved Instances that are terminated are billed until the end of their term.  
 
### EC2 Security
- When you deploy an Amazon EC2 instance, you are responsible for management of the guest operating system (including updates and security patches), any application software or utilities installed on the instances, and the configuration of the AWS-provided firewall (called a security group) on each instance. 
- With EC2, termination protection of the instance is disabled by default. This means that you do not have a safe-guard in place from accidentally terminating your instance. You must turn this feature on if you want that extra bit of protection.
- Amazon EC2 uses public–key cryptography to encrypt and decrypt login information. Public–key cryptography uses a public key to encrypt a piece of data, such as a password, and the recipient uses their private key to decrypt the data. The public and private keys are known as a key pair.
- You can encrypt your root device volume which is where you install the underlying OS. You can do this during creation time of the instance or with third-party tools like bit locker. Of course, additional or secondary EBS volumes are also encryptable as well.
- By default, an EC2 instance with an attached AWS Elastic Block Store (EBS) root volume will be deleted together when the instance is terminated. However, any additional or secondary EBS volume that is also attached to the same instance will be preserved. This is because the root EBS volume is for OS installations and other low-level settings. This rule can be modified, but it is usually easier to boot a new instance with a fresh root device volume than make use of an old one.


### EC2 Placement Groups
-  Placement groups balance the tradeoff between risk tolerance and network performance when it comes to your fleet of EC2 instances. The more you care about risk, the more isolated you want your instances to be from each other. The more you care about performance, the more conjoined you want your instances to be with each other. 
- There are three different types of EC2 placement groups:

  1.) Clustered Placement Groups
    - Clustered Placement Grouping is when you put all of your EC2 instances in a single availability zone. This is recommended for applications that need the lowest latency possible and require the highest network throughput.
    - Only certain instances can be launched into this group (compute optimized, GPU optimized, storage optimized, and memory optimized).
  
  2.) Spread Placement Groups
    - Spread Placement Grouping is when you put each individual EC2 instance on top of its own distinct hardware so that failure is isolated. 
    - Your VMs live on separate racks, with separate network inputs and separate power requirements. Spread placement groups are recommended for applications that have a small number of critical instances that should be kept separate from each other. 
  
  3.) Partitioned Placement Groups
    - Partitioned Placement Grouping is similar to Spread placement grouping, but differs because you can have multiple EC2 instances within a single partition. Failure instead is isolated to a partition (say 3 or 4 instances instead of 1), yet you enjoy the benefits of close proximity for improved network performance.
    - With this placement group, you have multiple instances living together on the same hardware inside of different availability zones across one or more regions.
    - If you would like a balance of risk tolerance and network performance, use Partitioned Placement Groups.
  
- Each placement group name within your AWS must be unique
- You can move an existing instance into a placement group guaranteed that it is in a stopped state. You can move the instance via the CLI or an AWS SDK, but not the console. You can also take a snapshot of the existing instance, convert it into an AMI, and launch it into the placement group where you desire it to be.

## Elastic Block Store (EBS)

### EBS Simplified
An Amazon EBS volume is a durable, block-level storage device that you can attach to a single EC2 instance. You can think of EBS as a cloud-based virtual hard disk. You can use EBS volumes as primary storage for data that requires frequent updates, such as the system drive for an instance or storage for a database application. You can also use them for throughput-intensive applications that perform continuous disk scans.

### EBS Key Details
- EBS volumes persist independently from the running life of an EC2 instance.
- Each EBS volume is automatically replicated within its Availability Zone to protect from both component failure and disaster recovery (similar to Standard S3).
- There are five different types of EBS Storage:
  - General Purpose (SSD)
  - Provisioned IOPS (SSD, built for speed)
  - Throughput Optimized Hard Disk Drive (magnetic, built for larger data loads)
  - Cold Hard Disk Drive (magnetic, built for less frequently accessed workloads)
  - Magnetic
- EBS Volumes offer 99.999% SLA.
- Wherever your EC2 instance is, your volume for it is going to be in the same availability zone
- An EBS volume can only be attached to one EC2 instance at a time.
- After you create a volume, you can attach it to any EC2 instance in the same availability zone.
- Amazon EBS provides the ability to create snapshots (backups) of any EBS volume and write a copy of the data in the volume to S3, where it is stored redundantly in multiple Availability Zones
- An EBS snapshot reflects the contents of the volume during a concrete instant in time.
- An image (AMI) is the same thing, but includes an operating system and a boot loader so it can be used to boot an instance. 
- AMIs can also be thought of as prebaked, launchable servers. AMIs are always used when launching an instance. 
- When you provision an EC2 instance, an AMI is actually the first thing you are asked to specify. You can choose a pre-made AMI or choose your own made from an EBS snapshot.
- You can also use the following criteria to help pick your AMI:
  - Operating System
  - Architecture (32-bit or 64-bit)
  - Region
  - Launch permissions
  - Root Device Storage (more in the relevant section below)
- You can copy AMIs into entirely new regions.
- When copying AMIs to new regions, Amazon won’t copy launch permissions, user-defined tags, or Amazon S3 bucket permissions from the source AMI to the new AMI. You must ensure those details are properly set for the instances in the new region.
- You can change EBS volumes on the fly, including the size and storage type

### EBS Storage Types: SSD vs. HDD
- SSD-backed volumes are built for transactional workloads involving frequent read/write operations, where the dominant performance attribute is IOPS. **Rule of thumb**: Will your workload be IOPS heavy? Plan for SSD.
- HDD-backed volumes are built for large streaming workloads where throughput (measured in MiB/s) is a better performance measure than IOPS. **Rule of thumb**: Will your workload be throughput heavy? Plan for HDD.

![hdd_vs_ssd](https://user-images.githubusercontent.com/13093517/84944872-76165b80-b0b4-11ea-819c-a93deb999ea2.png)


### EBS Snapshots
- EBS Snapshots are point in time copies of volumes. You can think of Snapshots as photographs of the disk’s current state and the state of everything within it.
- A snapshot is constrained to the region where it was created.
- Snapshots only capture the state of change from when the last snapshot was taken. This is what is recorded in each new snapshot, not the entire state of the server.
- Because of this, it may take some time for your first snapshot to be created. This is because the very first snapshot's change of state is the entire new volume. Only afterwards will the delta be captured because there will then be something previous to compare against. 
- EBS snapshots occur asynchronously which means that a volume can be used as normal while a snapshot is taking place.
- When creating a snapshot for a future root device, tt is considered best practices to stop the running instance where the original device is before taking the snapshot.
- The easiest way to move an EC2 instance and a volume to another availability zone is to take a snapshot.
- When creating an image from a snapshot, if you want to deploy a different volume type for the new image (e.g. General Pupose SSD -> Throughput Optimized HDD) then you must make sure that the virtualization for the new image is hardware-assisted.
- A short summary for creating copies of EC2 instances: Old instance -> Snapshot -> Image (AMI) -> New instance
- You cannot delete a snapshot of an EBS Volume that is used as the root device of a registered AMI. If the original snapshot was deleted, then the AMI would not be able to use it as the basis to create new instances. For this reason, AWS protects you from accidentally deleting the EBS Snapshot, since it could be critical to your systems. To delete an EBS Snapshot attached to a registered AMI, first remove the AMI, then the snapshot can be deleted.



### EBS Root Device Storage
- All AMI root volumes (where the EC2's OS is installed) are of two types: EBS-backed or Instance Store-backed
- When you delete an EC2 instance that was using an Instance Store-backed root volume, your root volume will also be deleted. Any additional or secondary volumes will persist however.
- If you use an EBS-backed root volume, the root volume will not be terminated with its EC2 instance when the instance is brought offline. EBS-backed volumes are not temporary storage devices like Instance Store-backed volumes.
- EBS-backed Volumes are launched from an AWS EBS snapshot, as the name implies
- Instance Store-backed Volumes are launched from an AWS S3 stored template. They are ephemeral, so be careful when shutting down an instance!
- Secondary instance stores for an instance-store backed root device must be installed during the original provisioning of the server. You cannot add more after the fact. However, you can add EBS volumes to the same instance after the server's creation.
- With these drawbacks of Instance Store volumes, why pick one? Because they have a very high IOPS rate. So while an Instance Store can't provide data persistence, it can provide much higher IOPS compared to network attached storage like EBS. 
- Further, Instance stores are ideal for temporary storage of information that changes frequently such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.
- When to use one over the other?
  - Use EBS for DB data, critical logs, and application configs.
  - Use instance storage for in-process data, noncritical logs, and transient application state.
  - Use S3 for data shared between systems like input datasets and processed results, or for static data needed by each new system when launched.

### EBS Encryption
- EBS encryption offers a straight-forward encryption solution for EBS resources that doesn't require you to build, maintain, and secure your own key management infrastructure.
- It uses AWS Key Management Service (AWS KMS) customer master keys (CMK) when creating encrypted volumes and snapshots. 
- You can encrypt both the root device and seconary volumes of an EC2 instance. When you create an encrypted EBS volume and attach it to a supported instance type, the following types of data are encrypted:
  - Data at rest inside the volume
  - All data moving between the volume and the instance
  - All snapshots created from the volume
  - All volumes created from those snapshots
- EBS encrypts your volume with a data key using the AES-256 algorithm. 
- Snapshots of encrypted volumes are naturally encrypted as well. Volumes restored from encrypted snapshots are also encrypted too. You can only share unencrypted snapshots.
- The old way of encrypting a root device was to create a snapshot of a provisioned EC2 instance. While making a copy of that snapshot, you then enabled encryption during the copy's creation. Finally, once the copy was encrypted, you then created an AMI from the encrypted copy and used to have an EC2 instance with encryption on the root device. Because of how complex this is, you can now simply encrypt root devices as part of the EC2 provisioning options.

## Elastic Network Interfaces (ENI)

### ENI Simplified
An elastic network interface is a networking component that represents a virtual network card. When you provision a new instance, there will be an ENI attached automatically and you can create and configure additional network interfaces if desired. When you move a network interface from one instance to another, network traffic is redirected to the new instance. 

### ENI Key Details
- ENI is used mainly for low-budget, high-availability network solutions
- However, if you suspect you need high network throughput then you can use Enhanced Networking ENI.
- Enhanced Networking ENI uses single root I/O virtualization to provide high-performance networking capabilities on supported instance types. SR-IOV provides higher I/O and lower throughput and it ensures higher bandwidth, higher packet per second (PPS) performance, and consistently lower inter-instance latencies. SR-IOV does this by dedicating the interface to a single instance and effectively bypassing parts of the Hypervisor which allows for better performance.
- Adding more ENIs won’t necessarily speed up your network throughput, but Enhanced Networking ENI will.
- There is no extra charge for using Enhanced Networking ENI and the better network performance it provides. The only downside is that Enhanced Networking ENI is not available on all EC2 instance families and types.
- You can attach a network interface to an EC2 instance in the following ways:
  - When it's running (hot attach)
  - When it's stopped (warm attach)
  - When the instance is being launched (cold attach).
- If an EC2 instance fails with ENI properly configured, you (or more likely,the code running on your behalf) can attach the network interface to a hot standby instance. Because ENI interfaces maintain their own private IP addresses, Elastic IP addresses, and MAC address, network traffic will begin to flow to the standby instance as soon as you attach the network interface on the replacement instance. Users will experience a brief loss of connectivity between the time the instance fails and the time that the network interface is attached to the standby instance, but no changes to the VPC route table or your DNS server are required.
- For instances that work with Machine Learning and High Performance Computing, use EFA (Elastic Fabric Adaptor). EFAs accelerate the work required from the above use cases. EFA provides lower and more consistent latency and higher throughput than the TCP transport traditionally used in cloud-based High Performance Computing systems. 
- EFA can also use OS-bypass (on linux only) that will enable ML and HPC applications to interface with the Elastic Fabric Adaptor directly, rather than be normally routed to it through the OS. This gives it a huge performance increase.
- You can enable a VPC flow log on your network interface to capture information about the IP traffic going to and from a network interface. 

## Security Groups

### Security Groups Simplified
Security Groups are used to control access (SSH, HTTP, RDP, etc.) with EC2. They act as a virtual firewall for your instances to control inbound and outbound traffic. When you launch an instance in a VPC, you can assign up to five security groups to the instance and security groups act at the instance level, not the subnet level. 

### Security Groups Key Details

- Security groups control inbound and outbound traffic for your instances (they act as a Firewall for EC2 Instances) while NACLs control inbound and outbound traffic for your subnets (they act as a Firewall for Subnets). Security Groups usually control the list of ports that are allowed to be used by your EC2 instances and the NACLs control which network or list of IP addresses can connect to your whole VPC.
- Everytime you make a change to a security group, that change occurs immediately
- Whenever you create an inbound rule, an outbound rule is created immediately. This is because Security Groups are *stateful*. This means that when you create an ingress rule for a security group, a corresponding egress rule is created to match it. This is in contrast with NACLs which are *stateless* and require manual intervention for creating both inbound and outbound rules.
- Security Group rules are based on ALLOWs and there is no concept of DENY when in comes to Security Groups. This means you cannot explicitly deny or blacklist specific ports via Security Groups, you can only implicitly deny them by excluding them in your ALLOWs list
- Because of the above detail, everything is blocked by default. You must go in and intentionally allow access for certain ports. 
- Security groups are specific to a single VPC, so you can't share a Security Group between multiple VPCs. However, you can copy a Security Group to create a new Security Group with the same rules in another VPC for the same AWS Account.
- Security Groups are regional and can span AZs, but can't be cross-regional.
- Outbound rules exist if you need to connect your server to a different service such as an API endpoint or a DB backend. You need to enable the ALLOW rule for the correct port though so that traffic can leave EC2 and enter the other AWS service.
- You can attach multiple security groups to one EC2 instance and you can have multiple EC2 instances under the umbrella of one security group
- You can specify the source of your security group (basically who is allowed to bypass the virtual firewall) to be a single **/32** IP address, an IP range, or even a separate security group.
- You cannot block specific IP addresses with Security Groups (use NACLs instead)
- You can increase your Security Group limit by submitting a request to AWS

## Web Application Firewall (WAF)

### WAF Simplified
AWS WAF is a web application that lets you allow or block the HTTP(s) requests that are bound for CloudFront, API Gateway, Application Load Balancers, EC2, and other Layer 7 entrypoints into your AWS environment. AWS WAF gives you control over how traffic reaches your applications by enabling you to create security rules that block common attack patterns, such as SQL injection or cross-site scripting, and rules that filter out specific traffic patterns that you can define. WAF's default rule-set addresses issues like the OWASP Top 10 security risks and is regularly updated whenever new vulnerbilities are discovered.

### WAF Key Details
- As mentioned above, WAF operates as a Layer 7 firewall. This grants it the ability to monitor granular web-based conditions like URL query string parameters. This level of detail helps to detect both foul play and honest issues with the requests getting passed onto your AWS environment.
- With WAF, you can set conditions such as which IP addresses are allowed to make what kind of requests or access what kind of content.
- Based off of these conditions, the corresponding endpoint will either allow the request by serving the requested content or return an HTTP 403 Forbidden status.
- WAF achieves its functionality by either:
  - Allowing all requests except for the ones you specified
  - Blocking all requests except for the ones you specified
  - Counting the requests that match the properties you specified

### WAF Protection Capabilities
- The web request characteristics that can be used to block access:
  - The IP address that a request originates from
  - The country that a request originates from
  - The values found in the request headers
  - Any strings that appear in the request (either specific strings or strings that match a regex pattern)
  - The length of the request
  - Any presence of SQL code (likely a SQL injection attempt)
  - Any presence of a script (likely a cross-site scripting attempt)
- You can also use NACLs to block malicious IP addresses, prevent SQL injections / XSS, and block requests from specific countries. However, it is good form to practice defense in depth. 
- Denying or blocking malicious users at the WAF level has the added advantage of protecting your AWS ecosystem at its outermost border.

## CloudWatch

### CloudWatch Simplified
Amazon CloudWatch is a monitoring and observability service. It provides you with data and actionable insights to monitor your applications, respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health.

### CloudWatch Key Details
- CloudWatch collects monitoring and operational data in the form of logs, metrics, and events.
- You can use CloudWatch to detect anomalous behavior in your environments, set alarms, visualize logs and metrics side by side, take automated actions, troubleshoot issues, and discover insights to keep your applications
running smoothly.
- Within the compute domain, CloudWatch can inform you about the health of EC2 instances, Autoscaling Groups, Elastic Load Balancers, and Route53 Health Checks.
Within the storage and content delivery domains, CloudWatch can inform you about the health of EBS Volumes, Storage Gateways, and CloudFront.
- With regards to EC2, CloudWathc can only monitor host level metrics such as CPU, network, disk, and status checks for insights like the health of the underlying hypervisor.
- CloudWatch is *NOT* CloudTrail so it is important to know that only CloudTrail can monitor AWS access for security and auditing reasons. CloudWatch is all about performance. CloudTrail is all about auditing.
- CloudWatch with EC2 will monitor events every 5 minutes by default, but you can have 1 minute intervals if you use Detailed Monitoring.

![Screen Shot 2020-06-17 at 8 16 23 PM](https://user-images.githubusercontent.com/13093517/84963455-71af6a00-b0d7-11ea-8168-15dd791bf000.png)

- You can customize your CloudWatch dashboards for insights.
- There is a multi-platform CloudWatch agent which can be installed on both Linux and Windows-based instances. This agent enables you to select the metrics to be collected, including sub-resource metrics such as per-CPU core. You can use this single agent to collect both system metrics and log files from Amazon EC2 instances and on-premises servers.
- The following metrics are not collected from EC2 instances via CloudWatch:
  - Memory utilization
  - Disk swap utilization
  - Disk space utilization
  - Page file utilization
  - Log collection
- If you need the above information, then you can retrieve it via the official CloudWatch agent or you can create a custom metric and send the data on your own via a custom script.
- CloudWatch's key purpose:
  - Collect metrics
  - Collect logs
  - Collect events
  - Create alarms
  - Create dashboards

### CloudWatch Logs
- You can use Amazon CloudWatch Logs to monitor, store, and access your log files from Amazon EC2 instances, AWS CloudTrail, Amazon Route 53, and other sources. You can then retrieve the associated log data from CloudWatch Logs.
- It helps you centralize the logs from all of your systems, applications, and AWS services that you use, in a single, highly scalable service.
- You can create log groups so that you join logical units of CloudWatch Logs together.
- You can stream custom log files for further insights.

### CloudWatch Events
- Amazon CloudWatch Events delivers a near real-time stream of system events that describe changes in AWS resources. 
- You can use events to trigger lambdas for example while using alarms to inform you that something went wrong.

### CloudWatch Alarms
- CloudWatch alarms send notifications or automatically make changes to the resources you are monitoring based on rules that you define. 
- For example, you can create custom CloudWatch alarms which will trigger notifications such as surpassing a set billing threshold.
- CloudWatch alarms have two states of either `ok` or `alarm`

### CloudWatch Metrics
- CloudWatch Metrics represent a time-ordered set of data points.
- These basically are a variable you can monitor over time to help tell if everything is okay, e.g. Hourly CPU Utilization.
- CloudWatch Metrics allows you to track high resolution metrics at sub-minute intervals all the way down to per second.

### CloudWatch Dashboards
- CloudWatch dashboards are customizable home pages in the CloudWatch console that you can use to monitor your resources in a single view
- These dashboards integrate with CloudWatch Metrics and CloudWatch Alarms to create customized views of the metrics and alarms for your AWS resources.


## CloudTrail

### CloudTrail Simplified
AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account. With it, you can log, continuously monitor, and retain account activity related to actions across your AWS infrastructure. CloudTrail provides event history of your AWS account activity, including actions taken through the AWS Management Console, AWS SDKs, command line tools, API calls, and other AWS services. It is a regional service, but you can configure CloudTrail to collect trails in all regions.

### CloudTrail Key Details
- CloudTrail Events logs API calls or activities. 
- CloudTrail Events stores the last 90 days of events in its Event History. This is enabled by default and is no additional cost.
- This event history simplifies security analysis, resource change tracking, and troubleshooting.
- There are two types of events that can be logged in CloudTrail: management events and data events. 
- Management events provide information about management operations that are performed on resources in your AWS account. 
- Think of Management events as things normally done by people when they are in AWS. Examples:
  - a user sign in
  - a policy changed
  - a newly created security configuration
  - a logging rule deletion
- Data events provide information about the resource operations performed on or in a resource. 
- Think of Data events as things normally done by software when hitting various AWS endpoints. Examples:
  - S3 object-level API activity
  - Lambda function execution activity 
- By default, CloudTrail logs management events, but not data events. 
- By default, CloudTrail Events log files are encrypted using Amazon S3 server-side encryption (SSE). You can also choose to encrypt your log files with an AWS Key Management Service (AWS KMS) key. As these logs are stored in S3, you can define Amazon S3 lifecycle rules to archive or delete log files automatically. If you want notifications about log file delivery and validation, you can set up Amazon SNS notifications.

## Elastic File System (EFS)

### EFS Simplified 
EFS provides a simple and fully managed elastic NFS file system for use within AWS. EFS automatically and instantly scales your file system storage capacity up or down as you add or remove files without disrupting your application.

### EFS Key Details 
- In EFS, storage capacity is elastic (grows and shrinks automatically) and its size changes based on adding or removing files.
- While EBS mounts one EBS volume to one instance, you can attach one EFS volume across multiple EC2 instances.
- The EC2 instances communicate to the remote file system using the NFSv4 protocol. This makes it required to open up the NFS port for our security group (EC2 firewall rules) to allow inbound traffic on that port.
- Within an EFS volume, the mount target state will let you know what instances are available for mounting
- With EFS, you only pay for the storage that you use so you pay as you go. No pre-provisioning required.
- EFS can scale up to the petabytes and can support thousands of concurrent NFS connections.
- Data is stored across multiple AZs in a region and EFS ensures read after write consistency.
- It is best for file storage that is accessed by a fleet of servers rather than just one server

## Amazon FSx for Windows

### Amazon FSx for Windows Simplified
Amazon FSx for Windows File Server provides a fully managed native Microsoft File System.

### Amazon FSx for Windows Key Details
- With FSx for Windows, you can easily move your Windows-based applications that require file storage in AWS.
- It is built on Windows Server and exists solely for Microsoft-based applications so if you need SMB-based file storage then choose FSx.
- FSx for Windows also permits connectivity between on-premise servers and AWS so those same on-premise servers can make use of Amazon FSx too.
- You can use Microsoft Active Directory to authenticate into the file system.
- Amazon FSx for Windows provides multiple levels of security and compliance to help ensure your data is protected. Amazon FSx automatically encrypts your data at-rest and in-transit.

## Amazon FSx for Lustre

### Amazon FSx for Lustre Simplified
Amazon FSx for Lustre makes it easy and cost effective to launch and run the open source Lustre file system for high-performance computing applications. With FSx for Lustre, you can launch and run a file system that can proccess massive data sets at up to hundreds of gigabytes per second of throughput, millions of IOPS, and sub-millisecond latencies.

### Amazon FSx for Lustre Key Details
- FSx for Lustre is compatible with the most popular Linux-based AMIs, including Amazon Linux, Amazon Linux 2, Red Hat Enterprise Linux (RHEL), CentOS, SUSE Linux and Ubuntu.
- Since the Lustre file system is designed for high-performance computing workloads that typically run on compute clusters, choose EFS for normal Linux file system if your requirements don't match this use case.
- FSx Lustre has the ability to store and retrieve data directly on S3 on its own.

## Relational Database Service (RDS)

### RDS Simplified
RDS is a managed service that makes it easy to set up, operate, and scale a relational database in AWS. It provides cost-efficient and resizable capacity while automating or outsourcing time-consuming administration tasks such as hardware provisioning, database setup, patching and backups.

### RDS Key Details
- RDS comes in six different flavors:
  - SQL Server
  - Oracle
  - MySQL Server
  - PostgreSQL
  - MariaDB
  - Aurora
- Think of RDS as the DB engine in which various DBs sit on top of.
- RDS has two key features when scaling out:
  - Read replication for improved performance
  - Multi-AZ for high availability
- In the database world, *Online Transaction Processing (OLTP)* differs from *Online Analytical Processing (OLAP)* in terms of the type of querying that you would do. OLTP serves up data for business logic that utimately composes the core functioning of your platform or application. OLAP is to gain insights into the data that you have stored in order to make better strategic decisions as a company.
- RDS runs on virtual machines, but you do not have access to those machines. You cannot SSH into an RDS instance so therefore you cannot patch the OS. This means that AWS  isresponsible for the security and maintenance of RDS. You can provision an EC2 instance as a database if you need or want to manage the underlying server yourself, but not with an RDS engine.
- Just because you cannot access the VM directly, it does not mean that RDS is serverless. There is Aurora serverless however (explained below) which serves a niche purpose.
- SQS queues can be used to store pending database writes if your application is struggling under a high write load. These writes can then be added to the database when the database is ready to process them. Adding more IOPS will also help, but this alone will not wholly eliminate the chance of writes being lost. A queue however ensures that writes to the DB do not become lost.


### RDS Multi-AZ
- Disaster recovery in AWS always looks to ensure standby copies of resources are maintained in a separate geographical area. This way, if a disaster (natural disaster, political conflict, etc.) ever struck where your original resources are, the copies would be unaffected.
- When you provision a Multi-AZ DB Instance, Amazon RDS automatically creates a primary DB instance and synchronously replicates the data to a standby instance in a different Availability Zone (AZ). Each AZ runs on its own physically distinct, independent infrastructure, and is engineered to be highly reliable.
- With a Multi-AZ configuration, EC2 connects to its RDS data store using a DNS address masked as a connection string. If the primary DB fails, Multi-AZ is smart enough to detect that failure and automatically update the DNS address to point at the secondary. No manual intervention is required and AWS takes care of swapping the IP address in DNS.
- Multi-AZ is supported for all DB flavors except aurora. This is because Aurora is completely fault-tolerant on its own.
- Multi-AZ feature allows for high availability across availability zones and not regions.
- During a failover, the recovered former primary becomes the new secondary and the promoted secondary becomes primary. Once the original DB is recovered, there will be a sync process kicked off where the two DBs mirror each other once to sync up on the new data that the failed former primary might have missed out on.
- You can force a failover for a Multi-AZ setup by rebooting the primary instance
- With a Multi-AZ RDS configuration, backups are taken from the standby.


### RDS Read Replicas
- Read Replication is exclusively used for performance enhancement.
- With a Read Replica configuration, EC2 connects to the RDS backend using a DNS address and every write that is received by the master database is also passed onto a DB secondary so that it becomes a perfect copy of the master. This has the overall effect of reducing the number of transactions on the master because the secondary DBs can be queried for the same data. 
- However, if the master DB were to fail, there is no automatic failover. You would have to manually create a new connection string to sync with one of the read replicas so that it becomes a master on its own. Then you’d have to update your EC2 instances to point at the read replica. You can have up to have copies of your master DB with read replication.
- You can promote read replicas to be their very own production database if needed.
- Read replicas are supported for all six flavors of DB on top of RDS.
- Each Read Replica will have its own DNS endpoint. 
- Automated backups must be enabled in order to use read replicas.
- You can have read replicas with Multi-AZ turned on or have the read replica in an entirely separate region. You can have even have read replicas of read replicas, but watch out for latency or replication lag.
The caveat for Read Replicas is that they are subject to small amounts of replication lag. This is because they might be missing some of the latest transactions as they are not updated as quickly as primaries. Application designers need to consider which queries have tolerance to slightly stale data. Those queries should be executed on the read replica, while those demanding completely up-to-date data should run on the primary node.


### RDS Backups
- When it comes to RDS, there are two kinds of backups:
  - automated backups
  - database snapshots
- **Automated backups** allow you to recover your database to any point in time within a retention period (between one and 35 days). Automated backups will take a full daily snapshot and will also store transaction logs throughout the day. When you perform a DB recovery, RDS will first choose the most recent daily backup and apply the relevant transaction logs from that day. Within the set retention period, this gives you the ability to do a point in time recovery down to the precise second.
Automated backups are enabled by default. The backup data is stored freely up to the size of your actual database (so for every GB saved in RDS, that same amount will freely be stored in S3 up until the GB limit of the DB). Backups are taken within a defined window so latency might go up as storage I/O is suspended in order for the data to be backed up.
- **DB snapshots** are done manually by the administrator. A key different from automated backups is that they are retained even after the original RDS instance is terminated. With automated backups, the backed up data in S3 is wiped clean along with the RDS engine. This is why you are asked if you want to take a final snapshot of your DB when you go to delete it.
- When you go to restore a DB via automated backups or DB snapshots, the result is the provisioning of an entirely new RDS instance with its own DB endpoint in order to be reached.

### RDS Security
- You can authenticate to your DB instance using IAM database authentication. IAM database authentication works with MySQL and PostgreSQL. With this authentication method, you don't need to use a password when you connect to a DB instance. Instead, you use an authentication token. 
- An authentication token is a unique string that Amazon RDS generates on request. Authentication tokens have a lifetime of 15 minutes. You don't need to store user credentials in the database because authentication is managed externally using IAM.
- IAM database authentication provides the following benefits:
  - Network traffic to and from the database is encrypted using Secure Sockets Layer (SSL).
  - You can use IAM to centrally manage access to your database resources, instead of managing access individually on each DB instance.
  - For applications running on Amazon EC2, you can use profile credentials specific to your EC2 instance to access your database instead of a password, for greater security
- Encryption at rest is supported for all six flavors of DB for RDS. Encryption is done using the AWS KMS service. Once the RDS instance is encryption enabled, the data in the DB becomes encrypted as well as all backups (automated or snapshots) and read replicas.
- After your data is encrypted, Amazon RDS handles authentication of access and decryption of your data transparently with a minimal impact on performance. You don't need to modify your database client applications to use encryption. 
- Amazon RDS encryption is currently available for all database engines and storage types. However, you need to ensure that the underlying instance type supports DB encryption.
- You can only enable encryption for an Amazon RDS DB instance when you create it, not after the DB instance is created and 
DB instances that are encrypted can't be modified to disable encryption. 

### RDS Enhanced Monitoring
- RDS comes with an Enhanced Monitoring feature. Amazon RDS provides metrics in real time for the operating system (OS) that your DB instance runs on. You can view the metrics for your DB instance using the console, or consume the Enhanced Monitoring JSON output from CloudWatch Logs in a monitoring system of your choice. 
- By default, Enhanced Monitoring metrics are stored in the CloudWatch Logs for 30 days. To modify the amount of time the metrics are stored in the CloudWatch Logs, change the retention for the RDSOSMetrics log group in the CloudWatch console.
- Take note that there are key differences between CloudWatch and Enhanced Monitoring Metrics. CloudWatch gathers metrics about CPU utilization from the hypervisor for a DB instance, and Enhanced Monitoring gathers its metrics from an agent on the instance. As a result, you might find differences between the measurements, because the hypervisor layer performs a small amount of work that can be picked up and interpreted as part of the metric.

## Aurora

### Aurora Simplified
Aurora is the AWS flagship DB known to combine the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. It is a MySQL/PostgreSQL-compatible RDBMS that provides the security, availability, and reliability of commercial databases at 1/10th the cost of competitors. It is far more effective as an AWS database due to the 5x and 3x performance multipliers for MySQL and PostgreSQL respectively.

### Aurora Key Details
- In case of an infrastructure failure, Aurora performs an automatic failover to to a replica of its own.
- Amazon Aurora typically involves a cluster of DB instances instead of a single instance. Each connection is handled by a specific DB instance. When you connect to an Aurora cluster, the host name and port that you specify point to an intermediate handler called an endpoint. Aurora uses the endpoint mechanism to abstract these connections. Thus, you don't have to hardcode all the hostnames or write your own logic for load-balancing and rerouting connections when some DB instances aren't available.
- By default, there are 2 copies in a minimum of 3 availability zones for 6 copies total for all of your Aurora data. This makes it possible for it to handle the potential loss of up to 2 copies of your data without impacting write availability and up to 3 copies of your data without impacting read availability.
- Aurora storage is self-healing and data blocks and disks are continuously scanned for errors. If any are found, those errors are repaired automatically.
- Aurora replication differs from RDS replicas in the sense that it is possible for Aurora's replicas to be be both a standby as part of a multi-AZ configuration as well as a target for read traffic. In RDS, the multi-AZ standby cannot be configured to be a read endpoint and only read replicas can serve that function.
- With Aurora replication, you can have up to fifteen copies. If you want downstream MySQL or PostgreSQL as you replicated copies, then you can only have 5 or 1.
- Automated failover is only possible with Aurora read replication
- For more on the differences between RDS replication and Aurora Replication, please consult the following:

![Screen Shot 2020-06-18 at 3 02 39 PM](https://user-images.githubusercontent.com/13093517/85061446-d240b480-b174-11ea-9dc4-f40d82743250.png)

- Automated backups are always enabled on Aurora instances and backups don’t impact DB performance. You can also take snapshots which also don’t impact performance. Your snapshots can be shared across AWS accounts.
- A common tactic for migrating RDS DBs into Aurora RDs is to create a read replica of a RDS MariaDB/MySQL DB as an Aurora DB. Then simply promote the Aurora DB into a production instance and delete the old MariaDB/MySQL DB.
- Aurora starts w/ 10GB and scales per 10GB all the way to 64 TB via storage autoscaling. Aurora's computing power scales up to 32vCPUs and 244GB memory

### Aurora Serverless
- Aurora Serverless is a simple, on-demand, autoscaling configuration for the MySQL/PostgreSQl-compatible editions of Aurora. With Aurora Serveress, your instance automatically scales up or down and starts on or off based on your application usage. The use cases for this service are infrequent, intermittent, and unpredictable workloads.
- This also makes it possible cheaper because you only pay per invocation
- With Aurora Serverless, you simply create a database endpoint, optionally specify the desired database capacity range, and connect your applications. 
- It removes the complexity of managing database instances and capacity. The database will automatically start up, shut down, and scale to match your application's needs. It will seamlessly scale compute and memory capacity as needed, with no disruption to client connections.

### Aurora Cluster Endpoints
- Using cluster endpoints, you map each connection to the appropriate instance or group of instances based on your use case.
- You can connect to cluster endpoints associated with different roles or jobs across your Aurora DB. This is because different instances or groups of instances perform different functions.
- For example, to perform DDL statements you can connect to the primary instance. To perform queries, you can connect to the reader endpoint, with Aurora automatically performing load-balancing among all the Aurora Replicas behind the reader endpoint. For diagnosis or tuning, you can connect to a different endpoint to examine details. 
- Since the entryway for your DB Instance remains the same after a failover, your application can resume database operation without the need for manual administrative intervention for any of your endpoints.

### Aurora Reader Endpoints
- Aurora Reader endpoints are a subset of the above idea of cluster endpoints. Use the reader endpoint for read operations, such as queries. By processing those statements on the read-only Aurora Replicas, this endpoint reduces the overhead on the primary instance. 
- There are up 15 Aurora Read Replicas because a Reader Endpoint to help handle read-only query traffic.
- It also helps the cluster to scale the capacity to handle simultaneous SELECT queries, proportional to the number of Aurora Replicas in the cluster. Each Aurora DB cluster has one reader endpoint.
- If the cluster contains one or more Aurora Replicas, the reader endpoint load-balances each connection request among the Aurora Replicas. In that case, you can only perform read-only statements such as SELECT in that session. If the cluster only contains a primary instance and no Aurora Replicas, the reader endpoint connects to the primary instance directly. In that case, you can perform write operations through the endpoint.
