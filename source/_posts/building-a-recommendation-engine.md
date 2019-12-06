---
title: Building a recommendation engine
cover_index: 2019/12/05/building-a-recommendation-engine/index.jpg
tile_color: '#fea832'
date: 2019-12-05 15:13:26
tags:
---
{% asset_img banner.png "Build a content-recommendation engine with Amazon Personalize" %}

In today's world, you can't browse anything without getting recommendations. Find a nice pair of shoes: recommendations. Watch a nice movie: recommendations. A recommendation engine is an informatiom filtering system that limits the amount and sort of content to the users likings. It's about tailoring a service for specific individuals rather than giving everyone the same, large amount of content. During this workshop, we'll dive deeper in the creation of a recommendation engine using Amazon Personalize. We were in the front row like the good students we are.

## What is Amazon Personalize ?
It's part of the AI portfolio, you don't have to worry about the underlying technologies. You get a model that is unique for your use case. Everything is super private, you can even encrypt with KMS. It is based on SageMaker, but wrapped as a nice service. This is good for developers that had no idea what they were doing during the SageMaker workshop.
Personalize relies on streaming user events, item metadata and user metadata, then get recommendations based on those. User interaction is the most important data that you'll stream into the service. User metadata can create stereotypes, and restrict recommendations since age for example can limit the amount of items suited for groups of people. For deployed models, you provision throughput, autoscaling will handle this fine. 
If the services does not know enough for a user, the user gets popular content. When you stream events in, the content will become more personalized. 
*One of the developers guiding this talk was from London. He was very funny, but also very talkative. 94% sure he voted against Brexit.* 

<!-- Note to self: setting up personalize with CloudFormation will need some custom resources 😔 
HRNN is the way to go for algorithms, the rest is nowhere near as good. Personalize is the cheapest way to use P3 instances. One of the key things to take from this session is that setting up Personalize takes like 16 million years. -->

## Algorithms to use
HRNN is the way to go for algorithms, the rest is nowhere near as good. Training the model with the algorithm of your choice happens the same way training SageMaker models happens. Personalize is the cheapest way to use P3 instances. One of the key things to take from this session is that setting up Personalize takes like 16 million years. Most of the time includes the provioning of resources, a minor part of the time is actual training. The good thing about this is that is takes acutally not that much longer to train the model with 10.000.000 records of input data than it does with 100.000 records.

## Cold start
<!-- Recommend new items with no data. Use via HRNN-Coldstart recipe. -->
When new users arrive, they have no history to base recommendations upon. Personalize will just return popular content. This can be setup using the HRNN-Coldstart recipe in Personalize.

## Useful resources
- [The workshop instructions](https://github.com/aws-samples/amazon-personalize-samples)
- [Session about video personalization](/2019/12/04/video-personalization/)