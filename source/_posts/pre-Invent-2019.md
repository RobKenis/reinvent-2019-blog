---
title: 'AWS pre:Invent 2019'
# cover_index: 2019/12/DAY/TITLE/index.png
date: 2019-12-01 11:45:00
tags:
---
The wait is over, re:Invent is around the corner. Just like me, most AWS teams cannot contain their excitement and have started releasing new features. This week leading up to re:Invent, also known as *AWS pre:Invent* is all about the new features that didn't make the keynote. But this doesn't mean they're not worth mentioning, so let's run over our top 5 of most heathwarming new features.

{% asset_img reinvent-banner.png "AWS re:Invent" %}

## Top 5 new features
1. AWS Lambda destinations
2. Java 11
3. Cloudwatch ServiceLens
4. Amazon CDK now available for Java and C#
5. Cloudwatch Synthetics

### AWS Lambda destinations
So you've been writing reusable code for a while now. Or so you thought, to send your response to a consumer (e.g. SQS), you still had to write code to deliver the message spcifically to that consumer. To mitigae this problem, AWS introduced [Lambda destinations](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-lambda-supports-destinations-for-asynchronous-invocations/), a solution to send a lambda result to a consumer without writing code. These consumers include: Lambda, SNS, SQS standard queue and Amazon EventBridge. Besides decoupling a part of your infrastructure, Lambda Destinations are supported in [https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-function.html](CloudFormation) right from the start. *(At the time of writing, DestinationConfig was not yet added to the CloudFormation documentation).* 
[Read more](https://aws.amazon.com/blogs/compute/introducing-aws-lambda-destinations/) about Lambda destinations.

### Java 11
With the release of Java 13 last september, it hit me that the bigger part of my production code is written in Java8. This isn't a bad thing, since Java8 still has a couple years of support, but it got me thinking about why it was still so far behind. One of the major reasons was the lack of Java11 support for [Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/). For lambda, this was not a problem, as my production lambda's are written in either nodejs or python. Well...AWS fixed both problems at once with the [release of Java 11 support for Beanstalk](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-elastic-beanstalk-launches-public-beta-corretto-al2-platforms/) and [Java11 support for Lambda](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-lambda-supports-java-11/). So go ahead and start writing those fancy Java11 applications.

### Cloudwatch ServiceLens

### Amazon CDK now availble for Java and C#

### Cloudwatch Synthetics

---
### Honorable mentions
- [SAM CLI simplified deployments](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-sam-cli-simplifies-deploying-serverless-applications-with-single-command-deploy/)
- [Elatic Beantstalk support for Spot Instances](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-elastic-beanstalk-adds-support-for-amazon-ec2-spot-instances/)
- [Lambda parallelization for event sources](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-lambda-supports-parallelization-factor-for-kinesis-and-dynamodb-event-sources/)
- [Cost categories](https://aws.amazon.com/about-aws/whats-new/2019/11/introducing-aws-cost-categories/)
- [Lambda failure-handling for event sources](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-lambda-supports-failure-handling-features-for-kinesis-and-dynamodb-event-sources/)
- [CodeBuild test reporting](https://aws.amazon.com/about-aws/whats-new/2019/11/aws-codebuild-adds-support-for-test-reporting/)