# CI/CD 

Server - is an **instance** that is stored in **DATA CENTER**

Application is **installed/deployed** in a server(EC2)

Developers are using micro-services these days to deploy the application 

Before micro-services monolithic services are used , where if one part of the application isn't working the whole application is affected.

**Lifecycle**:    **Development → Testing → Pre-Prod → Product Environment**
 
 developers share the file as executables or artifacts to QA for testing 

Role of DevOps - collaborate with developer and operation team and speed up the software delivery process.

### DevOps Phases:  7 C's 
  1.	Continuous Development 
  2.	Continuous Integration
  3.	Continuous Testing 
  4.	Continuous Deployment/Delivery  -  process of deploying an application into prod servers manually when it is completed testing and build stages.
  5.	Continuous Monitoring 
  6.	Continuous Feedback
  7.	Continuous Operations

## CI/CD: Continuous - Integration/Deployment

Methodology that automates the software development process focussing on integrating code changes frequently and automatically deploying those changes to testing or Prod Environment.

It aims to improve 
1.	Software quality
2.	Speed up delivery
3.	Reduce manual effort
   
Continuous INTEGRATION - Emphasizes integrating code changes from multiple developers into a shared repository frequently, ideally multiple times a day.
Automated builds & tests are run of these integrated changes to identify integration issues early.This helps developers to catch & fix bugs quickly and reduces integration problems.

Continuous DELIVERY - Automates the process of releasing code changes to a staging or testing environment , But a manual approval is often required before deploying into Production.

Continuous DEPLOYMENT - Automates deployment of code changes into Production after they pass all automated tests.


Popular tools - Jenkins, Gitlab CI, TeamCity,Bamboo CI, Azure devOps, AWS CICD

Despite popular tools, AWS has come up with AWS CICD - makes it easy, reduce complexity & time consumption.

## CI/CD Services by AWS:

### 1.	Codecommit 

  1.	AWS CodeCommit is a version control service hosted by Amazon Web Services that you can use to privately store and manage assets (such as documents, source code, and binary files) in the cloud.
  2.	saves the code changes made everyday in the source code management(SCM)
  3.	Helps in tracking code changes.
  4.	CodeCommit is a secure, highly scalable, managed source control service that hosts private Git repositories.
  5.	very similar to Git. Also this service is decommissioned from last year.
 
### 2.	Codebuild 

  1.	compiles your source code, runs unit tests, and produces artifacts that are ready to deploy.
  2.	eliminates the need to provision, manage, and scale your own build servers.
 
### 3.	Codedeploy

  1.	CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances, on-premises instances, serverless Lambda functions, or Amazon ECS services.
  2.	deploys application content that runs on a server and is stored in Amazon S3 buckets, GitHub repositories, or Bitbucket repositories.
  3.	CodeDeploy makes it easier for you to:
  1.	Rapidly release new features.
  2.	Update AWS Lambda function versions.
  3.	Avoid downtime during application deployment.
  4.	Handle the complexity of updating your applications, without many of the risks associated with error-prone manual deployments.
  5.	CodeDeploy works with various systems for configuration management, source control, continuous integration, continuous delivery, and continuous deployment.
 
### 4.	Codepipeline
  1.	continuous delivery service you can use to model, visualize, and automate the steps required to release your software.
  2.	You can quickly model and configure the different stages of a software release process.
  3.	CodePipeline automates the steps required to release your software changes continuously.
 
