# AWS S3 - Simple storage Services

## Amazon S3 is a managed cloud storage solution that enables you to store data as objects in a bucket.

## Amazon S3 designed for unstructured/unlimited way of store/process/retrieve an data over web access from Anywhere at anytime.

### Characteristics: 
  * It is an **Object Level Storage**.
  * S3 is **global service but region-specific**.
  * *Act* as a **Version Control management system**.
  * mostly Used for **static website hosting**.
  * **max size of an object** in S3 is of **5TB**.
    If a file is **more than 5GB** , you can upload the files using multipart upload (**multi part parallel upload**).

# Amazon S3 is designed to scale seamlessly and provide over **11 9s (99.999999999 percent) of durability**.

### Components of S3:
  * Buckets are **logical containers** for objects.
  * Objects - files stored in a bucket that can be almost any data file, such as documents, images or videos.
  * Bucket names are universal and must be unique across all existing bucket names in Amazon S3.

### What can be stored in s3?
  * realtime jpg, log, txt files.
  * videos.
  * csv files.
  * html files.

### Benefits:
  * High availability  - stores datat redundantly
  * Scalability - virtually store as many objects as you want
  * Security - none of your data is shared publicly, data is encryted in transit using SSL/TLS.
  * Cost Effective - low cost w.r.t storage classes that user chooses.
  * Performance - provides low-latency, data is accessed over the internet by **HTTP or HTTPS**, so you can retrieve data anytime from anywhere.
  * Flexible - data storage, backup, software delivery, archiving, recovery, website hosting, mobile applications, IOT devices & more.

### Bucket Type:
  * General Purpose - mix of storage class, redndantly stores objects across Multi-AZ.
  * Directory - recommended for low latency, fast processing of data use case, supports only Single AZ storage class.

### S3 Encryption Types:
  * SSE - S3 → server side encryption with amazon S3 managed keys.
  * SSE - KMS → Server side Encryption with AWS KMS managed Keys
  * SSE - C → Server side Encryption with Customer Provided Keys
  * Client Side Encryption → Encrypting before upload.

### Types of Amazon S3 storage classes:
1. S3 **Standard**: Designed for *high-performance, frequently accessed data*. Best for *active data, cloud applications, and content distribution*.
2. S3 **Standard-Infrequent** Access (S3 Standard-IA): For data accessed *less frequently* but requiring *rapid access* when needed. *Lower storage costs than Standard, but charges retrieval fees*.
3. S3 **Intelligent-Tiering**: *Automatically shifts data* between frequent and infrequent access tiers *based on usage* to save costs without performance impact.
4. S3 **Express One Zone**: *High-performance storage class* located in a *single Availability Zone*, offering the *lowest latency for the most frequently accessed data*.
5. S3 **One Zone-Infrequent** Access (S3 One Zone-IA): Similar to *S3 Standard-IA, stores data in a single Availability Zone* (20% lower cost), suitable for re-creatable data.
6. S3 **Glacier Archive Storage Classes**
   * S3 **Glacier Instant Retrieval**: suitable for *infrequently accessed data* but requiring *retrieval in milliseconds*, data kept for **90** days.
   * S3 **Glacier Flexible Retrieval**: Ideal for *archives with retrieval times from **minutes to hours*** (formerly S3 Glacier) , data kept for **180** days.
   * S3 **Glacier Deep Archive**: *Lowest-cost storage class*, meant for data kept for *7-10 years*, with *retrieval times within **12-48 hours***. 


     
