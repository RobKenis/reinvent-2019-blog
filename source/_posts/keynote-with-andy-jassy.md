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

## Redshift RA3 instances with Managed Storage
Scale redshift instances with more storage without needing to scale to more compute power. 
Pay-per-hour for compute and pay separately for storage. Only pay for what you use. 
> It's hard to scale without compromising performance. 
SSD throughput is scaling at a way faster rate than CPU processing rate. 

## AQUA 
- Advanced Query Accelerator
Hardware accelerated cache. Move the compute to the storage. 
This delivers 10x better query performance than anywhere else. 

## ElasticSearch Service
*Please let it be Cloudwatch Kibana*
### UltraWarm
Scale up to 3 PB of log data per cluster. 
Move unused data to S3. Save 90% of costs compared to what you do in ES today. 
If a query needs to pull data from S3, some nitro magic make the data accessible very quickly. 

## Databases
> Not your father's database
*Please be managed Casandra*
### Preview of Amazon Managed Cassandra Service
No clusters to be managed, pay on demand, uses same Cassandra drivers.

## Machine learning
Machine learning continues to grow on AWS. 

