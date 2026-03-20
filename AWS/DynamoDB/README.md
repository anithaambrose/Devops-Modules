# AWS Dynamo DB

Amazon DynamoDB is a **fully managed, serverless, NoSQL database service** designed for **high performnacee Apps with low latency & scalability & durability**.

It supports **key-value** and document data models, offering consistent **single-digit millisecond latency** at any scale.

Ideal for **high-traffic applications**, with **unstructured data** such as gaming app, IOT devices.

Handles automatic partitioning, data replication across availability zones.

Provides both on-demand and provisioned capacity modes. 


### Core Components

* Attributes: simplest element of dynamo DB , each attibute has name & value.

* Items: A group of attributes uniquely identifiable, similar to a row (individual data record).

* Tables: Collections of data , highest data structure in dynamo DB.

* Primary Key: Unique identifier for each item (Partition Key or Partition Key + Sort Key).

NOTE: Tables are schema-less meaning,items within a table do not need to have the same attribute, allows flexibility in data modelling.


### Common Use Cases:

* Gaming: Managing player data, leaderboards, and session history.
  
* Serverless Apps: Powering web, mobile, and IoT apps using AWS Lambda.

* E-commerce: Handling shopping carts and inventory management.
