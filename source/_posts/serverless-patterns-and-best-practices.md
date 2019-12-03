---
title: Serverless patterns and best practices
cover_index: 2019/12/DAY/TITLE/index.jpg
tile_color: '#fea832'
date: 2019-12-03 11:49:50
tags:
---
{% asset_img banner.png "Description goes here" %}

# What is not covered in the session
- Introduction to lambda
- Patterns for serverelss AI/ML
- Best practices for serverless at scale

# Operational responsibility model
Think of it as a spectrum. Not everything will be serverelss,  most of the time, it will be mix and match. 
'Create a serverless application' from the console became easy as fuck.
https://aws.amazon.com/quickstart/architecture/serverless-cicd-for-enterprise/
https://www.jeremydaly.com/serverless-microservice-patterns-for-aws/
https://github.com/alexcasalboni/aws-lambda-power-tuning

# Performance test
Memory tuning for lambda
Edge or regional endpoint for API Gateway. Removing the CDN in regional GW, it gets much faster *duh*

# Patterns
## Comfortable "REST"
Enable access logs, structure logs and instrument your code. Use Cloudwatch async metrics Embedded Metrics Format NEW
Annotate your code to enable tracing.
Regulate inbound access rate, enable throttling by default.
Manage Secrets with SSM, and authorize your consumers.
Cost effectiveness:
    - Regional endpoints for APIGW, especially if you dont need the CDN
    - Use ondemand scaling for dynamodb
        - If huge capacity is known beforehand, obviously enable provisioned throughput
    - Use lambda poesr tuning for perf/cost tuning
        - Beyond 1.7GB memory, lambda gets 2 cpus

### Cloudwatch Embeddded Metric Format
Dont spend CPU cycles to process logs and create metrics. Python and Nodejs library is open source.

## The "Cherry-pick"
Use appsync. Enable caching NEW
    In graphQL caching is hard, because the client picks what they want. With new AppSync caching, data can be cached at the resolver level or at the data level.
Use lambda for complex logic but not for just connecting point A to point B.
Use state machines for long transactions. Pipeline resolvers for simpler transactions.
Authorize at data level and use the database build for the purpose.

## Call me, "Maybe"
The famous webhook, call something when something happens. Limit lambda concurrency to avoid depleting the connection pool to relational databases. Lambda scales way quicker than RDS. Use kinesis as a buffer. Use lambda destinations for failed requests NEW. *If I have X retries, send the message to a destination. Something about lambda disect.* Obfuscate sensitive data on the stream. Kinesis can batch records for up to 5 minutes, very nice for low-volume traffic. You can integrate APIGW with pretty much any service, you dont need a lambda.

## The big "Fan"
Use fanout to leverage multiple consumers for pretty fast processing. Verify signature of SNS messages to make sure the message effectively came from SNS. Default SNS broadcasts messages to all consumers. Use messages filtering by consuming only messages with a certain message attribute. Compress and aggregate messages when possible. Consider *KINESIS* if possible for larger payloads

## They say "I'm a streamer"
Enable source stream record backup for kinesis firehose without invoking a lambda. Favor dedicated Data Firehose per context. Obfuscate sensitive data. Use parquet transformation at stream level. Transform payload at stream level from josn to parquet for example to be used with Athena. Use message filtering to prevent unwanted events. *Search for AWS global ingestion stream*

## The "Strangler"
Use an API to abstract implementaion details, which makes it easier to move parts behind the api. Centralize logs, metrics and tracing. Enforce authorization on the top level, most of the times this will be AD. *Read more about AD joke*. Gradually shift functionalities to new compute and database platforms. Dont straight up move everything to lambda, gradually do this to avoid disruption. 

https://github.com/aws-samples/aws-serverless-airline-booking
https://github.com/awslabs/realworld-serverless-application
https://github.com/awslabs/aws-lambda-powertools