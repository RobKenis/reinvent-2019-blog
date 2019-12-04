---
title: Serverless patterns and best practices
cover_index: 2019/12/03/serverless-patterns-and-best-practices/index.jpg
tile_color: '#f1e57a'
date: 2019-12-03 11:49:50
tags:
---
{% asset_img banner.jpg "Serverless patterns and best practices" %}

## Operational responsibility model
Not everything will be serverelss, most of the time, it will be mix and match. 'Create a serverless application' from the console became easy as 🥧.
Read more about getting started with serverless [here](https://aws.amazon.com/quickstart/architecture/serverless-cicd-for-enterprise/), [here](https://www.jeremydaly.com/serverless-microservice-patterns-for-aws/) and [here](https://github.com/alexcasalboni/aws-lambda-power-tuning).

## Performance test
Decide wether you need a regional or and edge-optimized endpoint in API Gateway. By removing the CDN in regional gateway, it gets much faster *duh*. Tweak your memory limits in lambda. Using Java in lambda in lambda doesn't mean you need to use all the RAM in the world plus a little extra.

## Patterns
### Comfortable "REST"
Enable access logs, structure logs and instrument your code. Use Cloudwatch async metrics Embedded Metrics Format **NEW**. Annotate your code to enable tracing. Regulate inbound access rate, enable throttling by default. Manage Secrets with SSM, and authorize your consumers.
Cost effectiveness:
    - Regional endpoints for API Gateway, especially if you dont need the CDN
    - Use ondemand scaling for dynamodb. If huge capacity is known beforehand, obviously enable provisioned throughput
    - Optimize cpu and memory for lambda. Beyond 1.7GB memory, lambda gets 2 cpus

### The "Cherry-pick"
Use AppSync. Enable caching **NEW**. In graphQL caching is hard, because the client picks what they want. With new AppSync caching, data can be cached at the resolver level or at the data level. Use lambda for complex logic but not for just connecting point A to point B. Use state machines for long transactionsm Pipeline resolvers for simpler transactions. Authorize at data level and use the database build for the purpose.

### Call me, "Maybe"
The famous webhook, call something when something happens. Limit lambda concurrency to avoid depleting the connection pool to relational databases. Lambda scales way quicker than RDS. Use kinesis as a buffer. Use lambda destinations for failed requests **NEW**. *If I have X retries, send the message to a destination.* Obfuscate sensitive data on the stream. Kinesis can batch records for up to 5 minutes, very nice for low-volume traffic. You can integrate API Gateway with pretty much any service, you dont need a lambda.

### The big "Fan"
Use fanout to leverage multiple consumers for pretty fast processing. Verify signature of SNS messages to make sure the message effectively came from SNS. Default SNS broadcasts messages to all consumers. Use messages filtering by consuming only messages with a certain message attribute. Compress and aggregate messages when possible. Consider *KINESIS* if possible for larger payloads

### They say "I'm a streamer"
Enable source stream record backup for kinesis firehose without invoking a lambda. Favor dedicated Data Firehose per context. Obfuscate sensitive data. Use parquet transformation at stream level. Transform payload at stream level from josn to parquet for example to be used with Athena. Use message filtering to prevent unwanted events. 
[Learn more](https://aws.amazon.com/blogs/networking-and-content-delivery/global-data-ingestion-with-amazon-cloudfront-and-lambdaedge/) about global data ingestion to Kinesis

### The "Strangler"
Use an API to abstract implementaion details, which makes it easier to move parts behind the api. Centralize logs, metrics and tracing. Enforce authorization on the top level of on-premise mainframes, most of the times this will be Active Directory. [Learn more](https://www.ad.nl/) about AD. Gradually shift functionalities to new compute and database platforms. Don't straight up move everything to lambda, gradually do this to avoid disruption. 

##### Usefull resources
https://github.com/aws-samples/aws-serverless-airline-booking
https://github.com/awslabs/realworld-serverless-application
https://github.com/awslabs/aws-lambda-powertools
