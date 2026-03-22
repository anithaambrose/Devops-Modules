# SNS & SQS

SNS & SQS
Amazon Simple Notification Service (Amazon SNS) is a managed service that provides message delivery from publishers to subscribers (also known as producers and consumers).

Publishers communicate asynchronously with subscribers by sending messages to a topic, which is a logical access point and communication channel.

Clients can subscribe to the SNS topic and receive published messages using a supported endpoint type, such as Amazon Kinesis Data Firehose, Amazon SQS, AWS Lambda, HTTP, email, mobile push notifications, and mobile text messages (SMS).

Simple Notification Service (SNS) sends the notifications through SMS or email to an Amazon Simple Queue Service (SQS), AWS lambda functions, or an HTTP endpoint. 

When the CPU utilization of an instance goes above 80%, the AWS cloudwatch alarm is triggered. 

This cloudwatch alarm activates the SNS topic hence notifying the subscribers about the high CPU utilization of the instance. 

SNS service has a topic that has a unique name. It acts as a logical access point and a communication channel between publishers and subscribers.

Benefits
SNS increases Durability. 

SNS increases Security.

SNS ensures accuracy.

SNS reduces and simplifies the cost.

SNS supports SMS in over 200 countries.

Features
Scalability: Simple Notification Service (SNS) had a capacity to handle millions of messages per second from the different sources.

Security: Simple Notification Service (SNS) is very secured and it also offers wide range of security offers.

High Availability: Simple Notification Service (SNS) is designed to have more durability which ensures the message are delivered without any latency.

Flexibility To Use: SNS supports a variety of transport protocols and can be used to send notifications to a variety of applications.


# SQS Workflow
SQS standards for Simple Queue Service offer asynchronous massaged-based communication between two services. 

Before SQS the communication between the two services was based upon the API calls after the SQS the event producer will notify the consumer in an asynchronous manner.

