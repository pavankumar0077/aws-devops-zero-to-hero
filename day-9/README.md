# AWS S3

## About 

What is Amazon S3?

**Simple Storage Service** is a scalable and secure cloud storage service provided by Amazon Web Services (AWS). It allows you to store and retrieve any amount of data from anywhere on the web.

What are S3 buckets?

S3 buckets are containers for storing objects (files) in Amazon S3. Each bucket has a unique name globally across all of AWS. You can think of an S3 bucket as a top-level folder that holds your data.

NOTE : **THE SECRET BEHIND THE SUCCESS (11 9's)**

# -----------------------------------------------------

Create s3 bucket
--
1) ![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/e9ad030c-3b77-4fd5-821b-e48dc7045065)
2) The name should be unique be'coz it is golbally accessable and it should be unquie through out the aws accounts available
3) S3 is global service, why we need to create it on region : S3 buckets are scoped in region but the context is gloablly accessed
4) Rest all options are same --> Create Bucket
5)  Let say if aws goes down the availablity zone goes down where s3 is created. What should we do the **99.99999999999** (11 9's) indicates the reliablity of the S3 bucket. 1 CR of objects in S3, anything we uploadin S3 is objects. In s3 our data never got delete, That is be'coz AWS use replication machinesm.
6)  What exactly AWS does --> Whereever we store the object in create multiple replicas of it availabilies zones, in data centers


# -----------------------------------------------------

Why use S3 buckets?

S3 buckets provide a reliable and highly scalable storage solution for various use cases. They are commonly used for backup and restore, data archiving, content storage for websites, and as a data source for big data analytics.

Key benefits of S3 buckets

S3 buckets offer several advantages, including:

    Durability and availability: S3 provides high durability and availability for your data.
    Scalability: You can store and retrieve any amount of data without worrying about capacity constraints.
    Security: S3 offers multiple security features such as encryption, access control, and audit logging.
    Performance: S3 is designed to deliver high performance for data retrieval and storage operations.
    Cost-effective: S3 offers cost-effective storage options and pricing models based on your usage patterns.
    Reliability : 11 9's realiable


Scalability : Store ALMOST unlimited data in a single bucket. However one object should not be more than 5 TB.
Tip:
Choose multipart uploads to upload an object if the size of the object is huge.

Security : S3 provides bucket policies, access control, and encryption settings are appropriately
configured.
Encrypt data at rest using server-side encryption options provided by S3. Additionally,
enable encryption in transit by using SSL/TLS for data transfers.
Enable access logging to capture detailed records of requests made to your S3 bucket.
Monitor access logs and configure alerts to detect any suspicious activities or unauthorized
access attempts.

Cost Effective :  Of Course it depends on the storage class that you use ...

![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/0c66ac73-612e-4414-bd03-b0443767fcaf)

REF LINK : https://aws.amazon.com/s3/storage-classes/

NOTE : S3 is like Version Control as well like github

NOTE : Bydefault if we use to store the same file it will replace the file,(If versioning is diabled) IF we enable versioning then it will store the pervious file as well and the new file as well.

![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/dd273caa-34ef-4981-b138-c560d784f812)

![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/dbcf22d2-8ee6-4e02-b3a8-0a2255725680)


Host satic website
--
1) Upload static page
2) ![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/d63fbfb0-4230-482b-abd2-e69830a7e98e)
3) Go to bucket properties --> Static website hosting  --> Enable it
4) ![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/e732fd46-7c76-4a0b-a9ad-d2d55bb86e18) add index.html page
5) Save changes
6) Now you will get an URL in the bucket properites properties, When we try to hit it it will show error forbidden eroor 403
7) Becuase while creating we have selected block public access --> uncheck ti
8) ![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/bdb1103a-f6aa-4f63-92e7-e158271de99c)
9) Now we have to add permission to access everyone in the internet
10) ![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/405aedba-9e21-46f6-88c1-fd183c16bb3d)
11) we need to give permisison to access the bucket to everyone in the internet
12) ![image](https://github.com/pavankumar0077/aws-devops-zero-to-hero/assets/40380941/a175aa4c-d475-4426-a976-0fcfd4617e0b)
13) NOTE : the page should be light weight -- like don't have more javascript that will do API calls -- We need to enable CORS (be'coz byfeault browser will block or reject it)  




## Creating and Configuring S3 Buckets

Creating an S3 bucket

To create an S3 bucket, you can use the AWS Management Console, AWS CLI (Command Line Interface), or AWS SDKs (Software Development Kits). You need to specify a globally
unique bucket name and select the region where you want to create the bucket.

Choosing a bucket name and region

The bucket name must be unique across all existing bucket names in Amazon S3. It should follow DNS naming conventions, be 3-63 characters long, and contain only lowercase
letters, numbers, periods, and hyphens. The region selection affects data latency and compliance with specific regulations.

Bucket properties and configurations

    Versioning: Versioning allows you to keep multiple versions of an object in the bucket. It helps protect against accidental deletions or overwrites.

Bucket-level permissions and policies

Bucket-level permissions and policies define who can access and perform actions on the bucket. You can grant permissions using IAM (Identity and Access Management) policies, 
which allow fine-grained control over user access to the bucket and its objects.

## Uploading and Managing Objects in S3 Buckets

Uploading objects to S3 buckets

You can upload objects to an S3 bucket using various methods, including the AWS Management Console, AWS CLI, SDKs, and direct HTTP uploads. 
Each object is assigned a unique key (name) within the bucket to retrieve it later.

Object metadata and properties

Object metadata contains additional information abouteach object in an S3 bucket. It includes attributes like content type, cache control, encryption settings, 
and custom metadata. These properties help in managing and organizing objects within the bucket.

File formats and object encryption

S3 supports various file formats, including text files, images, videos, and more. You can encrypt objects stored in S3 using server-side encryption (SSE). 
SSE options include SSE-S3 (Amazon-managed keys), SSE-KMS (AWS Key Management Service), and SSE-C (customer-provided keys).

Lifecycle management

Lifecycle management allows you to define rules for transitioning objects between different storage classes or deleting them automatically based on predefined criteria.
For example, you can move infrequently accessed data to a lower-cost storage class after a specified time or delete objects after a certain retention period.

Multipart uploads

Multipart uploads provide a mechanism for uploading large objects in parts, which improves performance and resiliency. You can upload each part in parallel and then
combine them to create the complete object. Multipart uploads also enable resumable uploads in case of failures.

Managing large datasets with S3 Batch Operations

S3 Batch Operations is a feature that allows you to perform bulk operations on large numbers of objects in an S3 bucket. 
It provides an efficient way to automate tasks such as copying objects, tagging, and restoring archived data.

## Advanced S3 Bucket Features

S3 Storage Classes

S3 offers multiple storage classes, each designed for different use cases and performance requirements:

![Screenshot 2023-07-06 at 7 16 51 PM](https://github.com/iam-veeramalla/aws-devops-zero-to-hero/assets/43399466/6b1ebcda-5b99-4358-ac1a-5bf559140571)


S3 Replication

S3 replication enables automatic and asynchronous replication of objects between S3 buckets in different regions or within the same region. 
Cross-Region Replication (CRR) provides disaster recovery and compliance benefits, while Same-Region Replication (SRR) can be used for data resilience and low-latency access.

S3 Event Notifications and Triggers

S3 event notifications allow you to configure actions when specific events occur in an S3 bucket. For example, you can trigger AWS Lambda functions, send messages to Amazon
Simple Queue Service (SQS), or invoke other services using Amazon SNS when an object is created or deleted.

S3 Batch Operations

S3 Batch Operations allow you to perform large-scale batch operations on objects, such as copying, tagging, or deleting, across multiple buckets. It simplifies managing large
datasets and automates tasks that would otherwise be time-consuming.

## Security and Compliance in S3 Buckets

S3 bucket security considerations

Ensure that S3 bucket policies, access control, and encryption settings are appropriately configured. Regularly monitor and audit access logs for unauthorized activities.

Data encryption at rest and in transit

Encrypt data at rest using server-side encryption options provided by S3. Additionally, enable encryption in transit by using SSL/TLS for data transfers.

Access logging and monitoring

Enable access logging to capture detailed records of requests made to your S3 bucket. Monitor access logs and configure alerts to detect any suspicious activities or unauthorized access attempts.


## S3 Bucket Management and Administration

S3 bucket policies

Create and manage bucket policies to control access to your S3 buckets. Bucket policies are written in JSON and define permissions for various actions and resources.

S3 access control and IAM roles

Use IAM roles and policies to manage access to S3 buckets. IAM roles provide temporary credentials and fine-grained access control to AWS resources.

S3 APIs and SDKs

Interact with S3 programmatically using AWS SDKs or APIs. These provide libraries and methods for performing various operations on S3 buckets and objects.

Monitoring and logging with CloudWatch

Utilize Amazon CloudWatch to monitor S3 metrics, set up alarms for specific events, and collect and analyze logs for troubleshooting and performance optimization.

S3 management tools

AWS provides multiple management tools, such as the AWS Management Console, AWS CLI, and third-party tools, to manage S3 buckets efficiently and perform operations like uploads, downloads, and bucket configurations.

## Troubleshooting and Error Handling

Common S3 error messages and their resolutions

Understand common S3 error messages like access denied, bucket not found, and exceeded bucket quota. Troubleshoot and resolve these errors by checking permissions, bucket configurations, and network connectivity.

Debugging S3 bucket access issues

Investigate and resolve issues related to access permissions, IAM roles, and bucket policies. Use tools like AWS CloudTrail and S3 access logs to identify and troubleshoot access problems.

Data consistency and durability considerations

Ensure data consistency and durability by understanding S3's data replication and storage mechanisms. Verify that data is correctly uploaded, retrieve objects using proper methods, and address any data integrity issues.

Recovering deleted objects

If an object is accidentally deleted, you can often recover it using versioning or S3 event notifications. Additionally, consider enabling Cross-Region Replication (CRR) for disaster recovery scenarios.
