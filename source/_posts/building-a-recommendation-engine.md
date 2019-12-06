---
title: Building a recommendation engine
cover_index: 2019/12/DAY/TITLE/index.jpg
tile_color: '#fea832'
date: 2019-12-05 15:13:26
tags:
---
{% asset_img banner.png "Build a content-recommendation engine with Amazon Personalize" %}

We were in the front row like the good students we are.

It's part of the AI portfolio, you don't have to worry about the underlying technologies. You get a model that is unique for your use case. Everything is super priate, you can even encrypt with KMS. It is based on SageMaker, but wrapped as a nice service. This is good for developers.
Personalize relies on streaming user events, item metadata and user metadata, then get recommendations based on those. User interaction is the most important data that you'll stream into the service. User metadata can create stereotypes, and restrict recommendations. For deployed models, you provision throughput, autoscaling will handle this fine. 
If the services does not know enough for a user, the user gets popular content. When you stream events in, the content will become more personalized. 
*The London dude is funny lol, but also very talkative. 94% sure he voted against Brexit.* 
__add part about jupyter notebook__

Note to self: setting up personalize will need some custom resources 😔 
HRNN is the way to go for algorithms, the rest is nowhere near as good. Personalize is the cheapest way to use P3 instances. One of the key things to take from this session is that setting up Personalize takes like 16 million years.

## Cold start
Recommend new items with no data. Use via HRNN-Coldstart recipe.

https://github.com/aws-samples/amazon-personalize-samples