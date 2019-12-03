---
title: Keynote with Andy Jassy
# cover_index: 2019/12/DAY/TITLE/index.jpg
tile_color: '#fea832'
date: 2019-12-03 08:21:11
tags:
---
<!-- {% asset_img banner.png "Description goes here" %} -->

It's all about moving fast, and doing it now.

## State of AWS
Closing out 2019, AWS remains te largest vendor with close to 45% market share.

## AWS Nitro system
Fully rebuild the hypervisor

## Chip innovations
Design new chips that bring more capabilities
### AWS Graviton chip
ARM-based chip, A1 instances.
### AWS Graviton2 chip
M6g, R6g, C6g instances.
40% better price per performance
### Inf1 instances for EC2
Machine learning optimized, the fastest inference in the cloud
Will be supported by ECS, EKS and Sagemaker
Integrated with frameworks like TensorFlow, PyTorch and MXNet.

## Containers
84% of the Kubernetes workload runs on AWS.
Don't worry about servers, use fargate. 
### Fargate now supported for EKS
Run your kubernetes hell without having to worry about servers.

## Networking
AWS Transit Gateway Multicast
Accelerated site to site vpn
Transit gateway inter-region peering
transit gateway network manager

> What are the things you take with you and what are the things you leave behind ?
On-premises cost a lot of money for the things you get. You have to spend a lot of money without getting the same features and security that the cloud can bring.]
Every industry is moving away from mainframes. They're slow, complicated and expensive. No one has mainframe knowlegde anymore.
Some companies pick the whole thing apart and launch them as microservices on AWS, some pick the things they need and move them to AWS.
People are trying to move away from oracle and SQL server; They're expensive. Microsoft is not prioritising what matters to the customers, look at all the damn licences. People are moving to open engines like mysql, mariadb and postgres. AWS offers same performance with open engines using AuroraDB. It is the fastest growing service on AWS. 

## Closing windows
People are moving from windows to linux. People dont want to pay the price anymore for windows. The linux community is alot wider. People are very happy when one entity owns the operating system. 

## Data
> Not your father's data requirements
Companies are moving from data silos to datalakes to make machine learning and analytics much easier. Data lakes are built on top of S3, because it is more reliable and scalable than anything else. Lots of this has to do with multi-AZ magic.  Other vendors offer low-grade availability zones because they're right next to eachother in the same building. S3 is the only object store to block public access on mulitpl levels and get an inventory on objects. It's the easiest object store to get data into through a million options. 
Read more about S3 intelligent tiering and S3 batch operations. S3 deep archive costs less than a dollar per TB. 

### S3 access points (new)
Simplifies managing data access. Assign a different access policy per application.  No more need to write a mile-long bucket policy. 

## Spectre
Query across redshift, S3 and operational databases.

## Redshift RA3 instances with Managed Storage NEW
Scale redshift instances with more storage without needing to scale to more compute power. 
Pay-per-hour for compute and pay separately for storage. Only pay for what you use. 
> It's hard to scale without compromising performance. 
SSD throughput is scaling at a way faster rate than CPU processing rate. 

## AQUA NEW
- Advanced Query Accelerator
Hardware accelerated cache. Move the compute to the storage. 
This delivers 10x better query performance than anywhere else. 

## ElasticSearch Service
*Please let it be Cloudwatch Kibana*
### UltraWarm NEW
Scale up to 3 PB of log data per cluster. 
Move unused data to S3. Save 90% of costs compared to what you do in ES today. 
If a query needs to pull data from S3, some nitro magic make the data accessible very quickly. 

## Databases
> Not your father's database
*Please be managed Casandra*
### Preview of Amazon Managed Cassandra Service NEW
No clusters to be managed, pay on demand, uses same Cassandra drivers.

## Machine learning
Machine learning continues to grow on AWS. 
Layers (of difficulty):
    - Frameworks for machine learning. TensorFlow, PyTorch and MXNet
        - AWS optmized TensorFlow is 20% faster than any other option (some very fancy private hardware not open to the public)
        - Optimized PyTorch is 22% faster, just like MXNet
    - SageMaker
        *Grab a screenshot around 9:45*
        - NEW: SageMaker Studio. Fully integrated development enviroment for SageMaker magic. Web-based IDE. This makes it much easier to write models.
        - NEW: SageMaker notebooks: one-click notebooks with Elatic Compute. No instances to provision, increase or decrease compute resources without interruption. 
        - NEW: SageMaker Experiments: Tuning models automatically. 
        - NEW: SageMaker Debugger: Real-time metrics of model performance, help understand and interprete models. Results can be viewed in SageMaker Studio. 
        > Looking at a model is like looking at a compiled binary. It makes no sense to the naked eye.
        - NEW: SageMaker Model Monitor: Detect concept drift in deployed models. Analyze and visualize models so you can detect concept drift.
### AutoML models
data -> *magic* -> model
Customers want automatic models with more insight in the actual model
#### SageMaker Autopilot NEW
Provide a csv with training data, Autopilot trains 50 unique models. SageMaker provides all the notebooks so you can tell how it actually works. All algorithms are ranked in a model leaderboard so you can choose which one you want. Autopilot gives you full control to tweak the models. 
> SageMaker studio is a giant leap forward being the first machine learning IDE
Collect all data and put a csv in S3. Create a new autopilot project in SageMaker Studio with the csv. SageMaker starts training 50 models and gives you an overview so you can pick the best one. You can look at the exact algorithms used by Autopilot with the Debugger information provided by SageMaker Debugger. After you pick your favorite model, you can deploy it right from SageMaker Studio. If SageMaker monitor finds any drift, it gives you an alert so you can train another set of models with new, fresh data. 

    - 3rd layer: AI Services

### Challenges of Fraud detection
Detecting fraud is very expensive and doesn't scale well because it uses little to no ML.
- Amazon Fraud Detector NEW
Send AWS your transactions and purchase history, they build a unique model for you.  That model will detect certain email domains for example based on the Amazon experience in fraud detection. These models will give you a fraud scoring on certain events. 

## Amazon CodeGuru NEW
Automatic code reviews and identify most expensive lines of code.
Add CodeGuru to pull request (CodeCommit and GitHub) as reviewer. Then CodeGuru goes over a couple models based on thousands of the most popular open source projects.
Detects AWS best practices like pagination and exception handling. Detects concurrency issues with non threadsafe classes. Incorrect handing of for example streams that can lead to injection attacks. 
CodeGuru profiler: Where can we find the most expensive lines of code. Intall an agent on the application that identifies CPU utilization and latency to help identify the most critical lines that can use optimization. CodeGuru creates a profile every 5 minutes.


*Rewatch the Andy Jassy keynote*