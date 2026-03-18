# AWS S3 - Simple storage Services


## Amazon S3 is a managed cloud storage solution that enables you to store data as objects in a bucket.

## Amazon S3 designed for unstructured/unlimited way of store/process/retrieve an data over web access fromAnywhere at anytime.

### Characteristics: 
  * It is an **Object Level Storage**.
  * S3 is **global service but region-specific**.
  * Act as a Version Control management system.
  * mostly Used for **static website hosting**.
  * **max size of an object** in S3 is of **5TB**.
    If a file is **more than 5GB** , you can upload the files using multipart upload (**multi part parallel upload**).

# Amazon S3 is designed to scale seamlessly and provide over **11 9s (99.999999999 percent) of durability**.

### Components of S3:
  * Buckets are **logical containers** for objects.
  * Objects - files stored in a bucket that can be almost any data file, such as documents, images or videos.
  * Bucket names are universal and must be unique across all existing bucket names in Amazon S3.

What can be stored in s3?
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

  1. Amazon S3 Standard - **default and the most expensive storage class*, most frequently accessed data.
  2. Amazon S3 Intelligent-Tiering. - 30 days 
  3. Amazon S3 Standard-Infrequent Access (Amazon S3 Standard-IA). - 30 days 
  4. Amazon S3 One Zone-Infrequent Access (Amazon S3 One Zone-IA). - 30 days 
  5. Amazon S3 Glacier. - 90 days 
       1. Instant Retrieval
       2. Flexible Retrieval
  6. Amazon S3 Glacier Deep Archive. - 180 days.

     
