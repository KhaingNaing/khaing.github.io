---
layout: page
title: "Data Storage"
parent: "AWS ML Certification Study Note"   
nav_order: 2
---

In this blog, we will detail all types of Storage servies available in AWS.

## Amazon S3

### Use Cases
- Backup and storage
- Disaster Recovery 
- Archive 
- Hybrid Cloud Storage
- Application hosting 
- Media hosting 
- Data Lakes & big data analytics 
- Software update delivery 
- Static website 

### Amazon S3 Bucket 
- allows to store objects (files) in buckets 
- must have a globally unique name across all regions all account
- defined at region-level (not global)

### Amazon S3 Objects
- objects (files) has a key (full path)
- key is composed of **prefix** + **object name**
  - e.g., s3://my-bucket/{prefix}/{object-name}
- object values are content of the body 
  - max size 5TB
  - use **multi-part upload** to upload obj > 5TB
- metadata 
- tags 
- version id (when versioning is enabled)

### Amazon s3 Security 
- **user-based**
  - **IAM policies** (for a specific user)
- **resource-based**
  - **bucket policies**
  - **object access control list (ACL)**
  - **bucket access control list (ACL)**
- an IAM princial can access s3 object if 
  - user IAM permissions **ALLOW** it **OR** the resource policy **ALLOW** it **AND** there is no explicit **DENY**
- **Encryption**: using s3 encryption keys
- e.g., control access to s3 bucket
  - public access - use bucket policy 
  - user access - IAM permissions
  - EC2 instance access - IAM Roles 
  - cross-account access - use bucket policy 

### Amazon s3 Versioning 
- can version files in s3
- enabled at bucket level 
- protect against unintended deletes; easy roll back to previous version
- Note:
  - any file prior to enable versioning has version **null**
  - suspend versioning does not delete the previous version 

### Amazon s3 Replication 
- **must enable versioning** in source and destination buckets
- must give proper IAM permissions to s3.
- after replication, only new objects are replicated
  - use s3 batch replication to replicate existing objects 
- for **DELETE** operations:
  - can replicate **delete markers**
  - deletions with a version ID are not replicated
- no "chaining" of replication

**Cross-Region Replication (CRR)**:
- use cases: compliance, lower latency access, replication across accounts

**Same-Region Replication (SRR)**:
- use cases: log aggregation, live replication between production and test accounts 

### S3 Storage Classes
Notation:
- GP: General Purpose
- IA: Infrequent Access
- Gla: Glacier
- IT: Intelligent-Tiering 

#### Classes
- **Amazon s3 Standard - General Purpose**: 
  - for frequent access 
  - low latency and high throughput 
- **Amazon s3 Infrequent Access**
  - **Amazon s3 Standard Infrequent Access**
  - **Amazon s3 One Zone Infrequent Access**
  - less frequent accessed but requires rapid access when needed
  - lower cost than s3 standard 
- **Amazon s3 Glacier**
  - **Amazon s3 Glacier Instant Retrieval**
  - **Amazon s3 Glacier Flexible Retrieval** 
  - **Amazon s3 Glacier Deep Archive** 
- **Amazon s3 Intelligent-Tiering**

**s3 Durability**: 
- measures how many objects lost
- high durability across multiple available zone
- same for all storage classes

**s3 availability**:
- measures how readily available a service is
- varies depending on storage class

|| standard GP | standard IA | One Zone IA | Gla IR | Gla FR | Gla DA | IT |
|-|-|-|-|-|-|-|-|
|use cases|big data analytics, mobile & gaming applications, content distribution|backup on-premises data|-|low cost object storage|-|-|-|
|durability|11 9's|
|availability|