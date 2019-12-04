---
title: Real World ML lifecycle with Amazon SageMaker
cover_index: 2019/12/04/real-world-ml-lifecycle-with-sagemaker/index.jpg
tile_color: '#fea832'
date: 2019-12-04 11:15:31
tags:
---
{% asset_img banner.png "Experience The Real-World ML Lifecyle With Amazon SageMaker" %}

ML Lifecycle
Feature selection - sample colleciton - model training - live inference - automated retraining
Feature selection: enumerate as much as you can, find as much feaatures as you can. Features mean input parameters btw, like age or height or gender for insurance companies. Work with what you have, gather new information takes a lot of work and that difficult yo. People were asking very difficult questions that were not related to the problem, which was a big problem in itself.

I was very excited to work with kinesis firehose, because I'm not rich enough to use it in my personal account.
Instructions are here: https://github.com/mike-calder/AIM368-Instructions
When creating an S3 bucket, there's a **create** button on the bottom left corner, this is what reinvent is all about folks!
Right now, you have to use a lambda to 'subscribe' Kineses to SNS, but my new buddy at AWS is going to upvote it on roadmaps.
Note to self: don't send SNS messages that can mess up your data.
Some people don't read comments and then fail horribly, like me. 
I have no idea what I'm doing, but things look promising.

Conclusion: I have no idea wtf I'm doing, but it looks nice. The trained model is stored in S3, a service that I do understand (a bit).