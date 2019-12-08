---
title: 're:Invent Recap'
cover_index: /2019/12/08/reinvent-recap/index.jpg
tile_color: '#7ecaf6'
date: 2019-12-08 18:41:39
tags:
---
{% asset_img banner.png "AWS re:Invent 2019 recap" %}

Another re:Invent in the books, a couple new releases and announcements. We've had a wonderful week and gained insights that we'll profit from for the upcoming year. Here's our recap or re:Invent 2019.

1. [Serverless](#Serverless)
2. [Machine Learning](#Machine-Learning)
3. [Computing at the Edge](#Computing-at-the-Edge)

## Serverless
With the introduction of *Kubernetes on Fargate*, you get another option to worry less about servers. Serverless remains the way to go to build and deploy your applications. Lambda remains the most scalable and cost-efficient option for short and infrequent executions. If you don't feel like Lambda is your thing, you can go for Fargate, a fully managed container service that handles server provioning behind the scenes so you can focus on building your application instead of patching servers.
### Related posts
- [Serverless patterns and best practices](/2019/12/03/serverless-patterns-and-best-practices/)
- [Building serverless micro-frontends](/2019/12/05/building-serverless-micro-frontends/)
- [Building full-stack serverless applications with Amplify](/2019/12/06/building-full-stack-applications-with-amplify/)

## Machine Learning
The machine learning portfolio on AWS is divided in 3 major categories. The high-level services like Rekognition, Polly and Lex that are targeted for developers without much knowlegde about machine learning. These services provide and API and do the machine learning part behind the scenes so the client has nothing to worry about. The second category is SageMaker, a service that lets you build and train your own models, but abstracts the layer of provisioning servers. And the third layer, the machine learning optimized AMI for the developers that really know what they're doing. This years re:Invent aimed on the second category, SageMaker. With a handfull of new releases, AWS brings SageMaker closer to the developers without AI and ML knowledge.
### Related posts
- [Video Personalization](/2019/12/04/video-personalization/)
- [Real World ML lifecycle with Amazon SageMaker](/2019/12/04/real-world-ml-lifecycle-with-sagemaker/)
- [Building a recommendation engine](/2019/12/05/building-a-recommendation-engine/)

## Computing at the Edge
If you have cilents all around the world, you have to give everyone the best experience possible. Deploying everything in one region and sacrificing response times for clients that happen to be far away, is no longer an option. With *Lambda@Edge* and *DynamoDB Global Tables*, you can execute your code as soon as your client hits a CloudFront Edge, bringing your application closer to your customers and improving response times.
### Related posts
- [Customizing content delivery at the Edge](/2019/12/04/customizing-content-at-the-edge/)


*Thank you for reading along with us. We'll see you again next year!*