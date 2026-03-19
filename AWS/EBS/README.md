# EBS - Amazon Elastic Block Storage

## Amazon Elastic Block Store (Amazon EBS) provides block level storage volumes for use with EC2 instances.

## EBS volumes behave like **raw, unformatted block devices** used for data that must be **quickly accessible and requires long-term persistence**.

### Amazon EBS volumes Characteristics:

  * Block-level storage device that you can attach to your instances like a physical hard drive
  * quickly accessible & zone specific - meaning data is stored to the zone close to the large group of users therefore provides low latency.
  * long term persistence - data doesnt get lost even when instance gets terminated , when Optimize instance termination protection is enabled.
  * flexible - capable of adding additional storage for a running instance

### Amazon EBS Volumes Types based on performance and cost requirements:

#### 1. SSD-backed volumes (gp3, gp2, io2, io1) for transactional, low-latency workloads (databases, boot volumes).

   * **General Purpose** SSD (gp2/gp3): Provides a *balance of price and performance* for a wide range of workloads.
   * **Provisioned IOPS** SSD (io1/io2): Designed for *critical, I/O-intensive applications requiring low latency* (e.g., Banking Apps, databases).
   
### 3. HDD-backed volumes (st1, sc1) for cost-effective, throughput-intensive, large-dataset workloads.

   * **Throughput Optimized** HDD (st1): Ideal for *frequently* accessed, *throughput-intensive workloads* like Big Data, streaming, and data warehouses and log processing.
   * **Cold** HDD (sc1): *Lowest cost storage* for *less frequently* accessed data or archival workloads.
     
### Benefits of using EBS volumes:
```
1.Data availability
2.Data persistence
3.Data encryption
4.Data security
5.Snapshots
6.Flexibility
```
# Snapshots: 

Amazon EBS provides the ability to *create snapshots (backups) of any EBS volume and **write a copy** of the data in the volume to **Amazon S3***, where it is **stored redundantly in multiple  Availability Zones**.

The volume *does not need to be attached to a running instance* in order to take a snapshot.

As we continue to write data to a volume, we can *periodically* create a snapshot of the volume to use as a baseline for new volumes.
  
These snapshots can be *used to create multiple new EBS volumes or move volumes across Availability Zones*.

Snapshots of *encrypted EBS volumes* are *automatically encrypted*.

Snapshots are *incremental backups*, meaning that only the blocks on the *volume that have changed after your most recent snapshot are saved*.

