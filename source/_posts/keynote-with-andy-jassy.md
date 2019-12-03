---
title: Keynote with Andy Jassy
cover_index: 2019/12/03/keynote-with-andy-jassy/index.jpg
tile_color: '#bada55'
date: 2019-12-03 08:21:11
tags:
---
{% asset_img banner.jpeg "Keynote with Andy Jassy" %}

It's all about moving fast, and doing it now. This remains one of the key concepts of AWS and it will stay that way throughout 2020. Don't be afraid to change up your systems as you will fall behind quicker than you realize. Like last year, Andy Jassy's keynote was full of new releases and a bunch of developers getting excited about new ways to put things in databases. Closing out 2019, AWS remains te largest vendor with close to 45% market share. Microsoft is in the rearview mirror, but far far away.

## AWS Nitro System
AWS released a new generation of ARM-based processors, which deliver a 40% better price per performance compared to the latest GPU based instances. Andy also used a lot of words that I did not understand, so to learn more about AWS Nitro, you can start [here](https://aws.amazon.com/ec2/nitro/).

<!-- ## Chip innovations
Design new chips that bring more capabilities
### AWS Graviton chip
ARM-based chip, A1 instances.
### AWS Graviton2 chip
M6g, R6g, C6g instances.
40% better price per performance
### Inf1 instances for EC2
Machine learning optimized, the fastest inference in the cloud
Will be supported by ECS, EKS and Sagemaker
Integrated with frameworks like TensorFlow, PyTorch and MXNet. -->

## Containers
84% of the Kubernetes workloads run on AWS. This is a massive amount, almost as big as the amount of developers that don't care about servers. To solve this problem, AWS launched [Fargate](https://aws.amazon.com/fargate/) last year. Fargate solves the problem of provisioning servers to run containerized workloads by provioning servers for you under the hood.
#### Fargate now supported for EKS **NEW**
With the release of Fargate support for EKS, you can now run your Kubernetes workloads on Fargate. So you can stop worrying about servers and clusters, while you can still question every choice you've ever made including the one about using Kubernetes.

## Networking
- [AWS Transit Gateway Multicast](https://aws.amazon.com/about-aws/whats-new/2019/12/run-ip-multicast-workloads-aws-transit-gateway/) **NEW**
- [Accelerated site to site VPN](https://aws.amazon.com/about-aws/whats-new/2019/12/announcing-accelerated-site-to-site-vpn-for-improved-vpn-performance/) **NEW**
- [Transit gateway inter-region peering](https://aws.amazon.com/about-aws/whats-new/2019/12/aws-transit-gateway-supports-inter-region-peering/) **NEW**
- [Transit gateway network manager](https://aws.amazon.com/about-aws/whats-new/2019/12/aws-announces-aws-transit-gateway-network-manager/) **NEW**

## Modernization
> Moving to the cloud is like moving house. What are the things you take with you and what are the things you leave behind ? - Andy Jassy, 2019

On-premises cost a lot of money for the things you get. You have to spend a lot of money without getting the same features and security that the cloud can bring. Every industry is moving away from mainframes. They're slow, complicated and expensive. No one has mainframe knowledge anymore. Some companies pick the whole thing apart and launch them as microservices on AWS, some pick the things they need and move them to AWS. People are trying to move away from Oracle and SQL server; They're expensive. Microsoft is not prioritising what matters to the customers, look at all the damn licences. People are moving to open engines like MySQL, MariaDB and Postgres. AWS offers same performance with open engines using AuroraDB. It is the fastest growing service on AWS. 

#### Closing windows
People are moving from Windows to Linux. People don't want to pay the price anymore for Windows. The Linux community is alot sophisticated. People are not very happy when one entity owns the operating system, looking at you, Bill Gates.

## Storage
> Not your father's data requirements. - Andy Jassy, 2019

Companies are moving from data silos to datalakes to make machine learning and analytics much easier. Data lakes are built on top of S3, because it is more reliable and scalable than anything else. Lots of this has to do with multi-AZ magic.  Other vendors offer low-grade availability zones because they're right next to eachother in the same building. S3 is the only object store to block public access on multiple levels and get an inventory on objects. It's the easiest object store to get data into through a million options. 

Read more about [S3 intelligent tiering](https://aws.amazon.com/about-aws/whats-new/2018/11/s3-intelligent-tiering/) and [S3 batch operations](https://aws.amazon.com/about-aws/whats-new/2018/11/s3-batch-operations/). [S3 deep archive](https://aws.amazon.com/blogs/aws/new-amazon-s3-storage-class-glacier-deep-archive/) costs less than a dollar per TB, which makes it the perfect candidate to store all your backups and other data that may take a while to retrieve, but must be stored for a long time.  

### S3 access points **NEW**
<!-- Simplifies managing data access. Assign a different access policy per application.  No more need to write a mile-long bucket policy.  -->
So you finally figured out how to implement security and access control on your S3 buckets. Your bucket policy is a work of art and your consumer is working flawlessly. But then you need to add a second client, and a third, and before you know, your bucket policy is a mile long *(or 1,60934 kilometers for users of the proper metric system)*. Introducing S3 access points, AWS claims to simplify access control to your bucket over a variety of clients.

[Read more](https://aws.amazon.com/blogs/aws/easily-manage-shared-data-sets-with-amazon-s3-access-points/) about S3 access points

## Databases
> Not your father's database. - Andy Jassy, 2019
### Redshift RA3 instances with Managed Storage **NEW**
<!-- Scale redshift instances with more storage without needing to scale to more compute power. 
Pay-per-hour for compute and pay separately for storage. Only pay for what you use. 
> It's hard to scale without compromising performance. 
SSD throughput is scaling at a way faster rate than CPU processing rate.  -->
`Disk will fill in 12 hours`. Your pages beeps, your heart rate rises, this alert sends shivers down your spine. You've been trained for this, you know what to do, so you turn on your laptop and open the AWS console. You navigate to the Redshift console and look for a way to increase disk space. And then it hits you, you have to increase the instance type aswell. This doesn't have to be reality, luckily AWS had the same thoughts. With the new [RA3 instances](https://aws.amazon.com/about-aws/whats-new/2019/12/amazon-redshift-announces-ra3-nodes-managed-storage/), you can scale storage and compute independently.

### Performance
It's hard to scale without compromising performance. SSD throughput is scaling at a way faster rate than CPU processing rate.
#### Advanced Query Accelerator **NEW**
Hardware accelerated cache. Move the compute to the storage. This delivers 10x better query performance than anywhere else. 

### ElasticSearch Service
> Please let it be Cloudwatch Kibana 🤞 - Kenneth De Win, 2019
#### UltraWarm **NEW**
Scale up to 3 PB of log data per cluster. Move unused data to S3. Save 90% of costs compared to what you do in ES today. If a query needs to pull data from S3, some Nitro magic make the data accessible very quickly. 

### Cassandra
> Please be managed Casandra 🤞 - Rob Kenis, 2019
#### Preview of Amazon Managed Cassandra Service **NEW**
No clusters to be managed, pay on demand, uses same Cassandra drivers. There's not much more to it. Finally use Cassandra without contemplating your career as a developer.

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

## Contact Lens for Amazon Connect NEW
Generates analytics on Amazon Connect, which is a managed contact center. Contact Lens captures calls analyzes if the conversation was positive or negative. Create dashboards containing overall satisfaction. 

## Amazon Kendra NEW
Configure data sources like Jira, box and google drive. Optionally provide a set of FAQs. Then sync and index the data, Kendra pulls in all data and builds an index. Kendra finds concepts and relations between content. Test and refine queries straight from the console. Deploy the Kendra web application or cut-past Kendra components in your existing application. Some natural language processing can understand questions like 'When is the helpdesk opened' to provide answers to your questions instead of some terrible confluence page.  

## AWS Outposts
Generally available today with Compute, Databases, Storage and more. *S3 coming soon* 
## AWS Local Zones NEW
Extension of an AWS region. AWS managed buildings with outputs close to you, so you can have single-digit latency with AWS workloads. 

## 5G
8 currencies:
- Speed is going up to 10Gb per second
- Latency goes down to 10ms
- Connect 10 million devices instead of 100 thousand
- ...
*(4G only had 2: speed and throughput)*
With 5G, bring the processing out to the edge. 

## AWS Wavelength NEW
Build applications that bring single-digit ms latency right as the edge embedded in 5G. Fewer hops to go from the device to the service. Right at the city aggregation site is AWS. 
*This part ended with an awkward hug around 10:47*

# Conclusion
A lot of people get nervous about change. It's scary how far behind you can become in a very short period of time. With what the cloud offers, you can build things that were never possible before. That is an opportunity unlike any other.

*Rewatch the Andy Jassy keynote*