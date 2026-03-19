# EFS - AWS Elastic File System

## EFS is a file-level, fully managed, storage provided by AWS  that can be accessed by multiple EC2 instances concurrently. 

Just like the AWS EBS, EFS is specially designed for **high throughput and low latency applications**.


### EFS Storage Classes:

1. Standard
     default storage class
     recommended for storing frequently accessed files.
     only charged for the amount of storage used.

2. Infrequent Access
      Cheaper storage space.
      Recommended for rarely accessed files.
      Increased latency when reading or writing files.

### Performance Modes in EFS:

1. **General Purpose**
      Offers low latency.
      Supports a maximum of 7000 IOPS.
      As a cloud watch metric, you can view the amount of IOPS your architecture uses and can switch to Max IOPS if required.

2. **Max I/O**:
      recommended when EFS needs over 7000 IOPS ,  unlimited I/O speed.

### Throughput Modes in EFS:

1. **Burst** Mode - Allows 100MBPS of burst speed per TB of storage.
2. **Provisioned** Mode - Users can decide the max burst speed of the EFS but are charged more when speeds go beyond the default limit.

### Advantages: 

1. scalable and elastic  -  scaling is done *automatically*.
2. Concurrent usage of storage - Multiple instances in AWS can access the EFS *simultaneously*.
3. High Availability - Within the same region, the EFS *replicates the data* to the multiple availability zones.
5. Serverless/Fully Managed: *No need* to manage infrastructure, file system servers, or software updates.
   
### Limitations of EFS:

* only supports the Network File System (NFS) protocol, so it can only be mounted and accessed by devices that support NFS.
* maximum file size of 47.9 TB.
* maximum throughput of 1000 MB/s per file system and a maximum of 16,000 IOPS per file system.
* maximum number of files and directories that can be created within a single file system, which is determined by the size of the file system.
  For example, a 1 TB file system can support up to about 20 million files and directories.

### Common Use Cases:
* Shared Content Repositories: Web serving, CMS (e.g., WordPress), and home directories.
* Container/Serverless Storage: Persistent storage for ECS, EKS, and AWS Lambda.
* Big Data & Analytics: Fast processing for large datasets.
* Backup & DevOps: Development environments and Database backups.

### EFS vs. Other AWS Storage:

#### EFS vs. EBS: EFS is designed for shared file access (NFS), while EBS (Elastic Block Store) is designed for high-performance block storage attached to a single EC2 instance.

#### EFS vs. S3: EFS provides a file system interface (hierarchical), while S3 is object storage. 

