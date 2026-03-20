# RDB - AWS Relational Database Service

Amazon Relational Database Service (RDS) is a **managed** cloud service from AWS that simplifies **setting up, operating, and scaling** relational databases .

RDBMS - (MySQL, PostgreSQL, Oracle, SQL Server, MariaDB, and Aurora). 

It **automates** time-consuming tasks like backups, patching, and infrastructure provisioning, making database administration highly efficient.

Port No for RDS - **3306**

### Key Features
* Automated Management: Handles patching, backups, and failover.
* Scalability: Single API call or console click to scale compute/storage.
* High Availability: Multi-AZ deployments for redundancy

  
### Key RDS Database Engine Types:

1. Amazon Aurora (MySQL/PostgreSQL) :   Offers *higher performance and availability* than standard MySQL/PostgreSQL.
   
2. MySQL:            *Popular open-source database* frequently used for web applications, content management systems, mobile apps and simple transactional operations.

3. PostgreSQL:       *Advanced open-source object-relational DBMS* known for **complex** data handling, JSON support, and extensibility.

4. MariaDB:          *community-developed, open-source fork of MySQL*, frequently used as a drop-in replacement, supported for many applications.6

5. Oracle:           A popular *commercial relational DBMS, supporting various editions and licensing models (BYOL or License Included).

6. SQL Server:       *Microsoft's commercial relational DB engine*, tailored for *enterprise-level applications* and *tightly integrated with Windows ecosystems*

### Supported Instance Classes

* General Purpose (e.g., db.m6g, db.m7g): Balanced CPU and memory.
  
* Memory Optimized (e.g., db.r5, db.r6g): Best for high-performance databases needing heavy memory.
  
* Burstable Performance (e.g., db.t3, db.t4g): Cost-effective for low-utilization scenarios. 


### Read Replica Confguration for high Availability & durability 

* Multi-AZ DB **instance** deployment (**2** instances)

      Multi-AZ deployments can have one standby or two standby DB instances. When the deployment has one standby DB instance, it's called a Multi-AZ DB instance deployment.

      A Multi-AZ DB instance deployment has one standby DB instance that provides failover support, but doesn't serve read traffic.

* Multi-AZ DB **Cluster** deployment (**3** instances)

      When the deployment has two standby DB instances, it's called a Multi-AZ DB cluster deployment.

      A Multi-AZ DB cluster deployment has standby DB instances that provide failover support and can also serve read traffic.

* **Single**-AZ DB instance deployment (**1** instances)

      Single instance deployment , which server both read and writes traffic & provide no failover support. 

### Amazon RDS Blue/Green Deployments:

A blue/green deployment creates a staging environment that copies the production environment.

In a blue/green deployment, the blue environment is the current production environment.

The green environment is the staging environment. The staging environment stays in sync with the current production environment using logical replication.


### Backups:

Amazon RDS **creates and saves automated backups** of the DB instance or Multi-AZ DB cluster during the **backup window** of the DB instance.

RDS creates a **storage volume snapshot** of the DB instance, backing up the *entire DB instance* and not just individual databases.

RDS *saves the automated backups of the DB* instance according to the **backup retention period** that you specify. 

If necessary, we can recover the DB instance to any point in time during the backup retention period.

### Automated backups follow these rules:

 1. DB instance must be in the **available state** for automated backups to occur.

    Automated backups don't occur while your DB instance is in a state other than available, for example, storage_full.

2. Automated backups don't occur while a DB snapshot copy is running in the same AWS Region for the same database.


