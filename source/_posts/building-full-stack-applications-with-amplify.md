---
title: Building full-stack serverless applications with Amplify
cover_index: /2019/12/06/building-full-stack-applications-with-amplify/index.png
tile_color: '#fea832'
date: 2019-12-06 09:23:43
tags:
---
{% asset_img banner.png "Building full-stack serverless applications with AWS Amplify" %}

AWS Amplify makes it easier to build and deploy serverless applications to AWS. [Amplify](https://github.com/aws-amplify/amplify-js) takes care of deploying resources using CloudFormation and makes developing applications easier, especially for new users.

[The workshop](https://github.com/aws-samples/aws-reinvent-2019-mobile-workshops/tree/master/MOB303) we attended and *almost* completed gives the perfect insights to get you started with Amplify. One of the key features of Amplify is that is does a lot of magic behind the screen. It creates CloudFormation templates from the little input that you provide it. Run `amplify add auth` for example and it sets up [AWS Cognito](https://aws.amazon.com/cognito/) with the required attributes to get you started with a login system for your users. To get you up and running quicky, this is perfect. On the other hand, Amplify has its own way to provision resources, it creates a nested CloudFormation stack for every part of your application. Some people have very strong opinions on this, Rob being one of them. But to test out new services, there is no easier option then using Amplify.