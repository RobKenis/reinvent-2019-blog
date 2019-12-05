---
title: Real World ML lifecycle with Amazon SageMaker
cover_index: 2019/12/04/real-world-ml-lifecycle-with-sagemaker/index.jpg
tile_color: '#fea832'
date: 2019-12-04 11:15:31
tags:
---
In Amazon warehouses, it's all about robotics. More than 200.000 robots are part of the workflow to get the massive variety of products to the customer. The constantly improve the movement and timings of these robots, a couple of very smart people have used machine learning to define their behaviour.
<!-- ML Lifecycle
Feature selection - sample colleciton - model training - live inference - automated retraining
Feature selection: enumerate as much as you can, find as much feaatures as you can. Features mean input parameters btw, like age or height or gender for insurance companies. Work with what you have, gather new information takes a lot of work and that difficult yo. People were asking very difficult questions that were not related to the problem, which was a big problem in itself. -->

## Machine Learning lifecycle
It all starts with the selection of features, the input parameters that you define your model upon. In case of Amazon, the features consist of product size and weight, placement of the product in the rack and many more. Once you've selected the features, it's time to start gathering samples. Collect as much data as you can about the input you've defined and the outcome they produce. After you've gone wild and collected all the information you can get, you're ready to start training your model. *This is the part where the people without ML knowledge, like me, got completely lost.*  Once you've trained your model using Jupyter Notebooks in SageMaker, just deploy it from the SageMaker console. This may take a while, but after waiting for a couple of minutes, you can start using the model to predict outcome of new data, this is also known as inference.

## TLDR: The workshop
The full instructions for the workshop can be found [here](https://github.com/mike-calder/AIM368-Instructions). People were asking very difficult questions that were not related to the problem, which was a big problem in itself. I was very excited to work with Kinesis firehose, because I'm not rich enough to use it in my personal account. I learned that when creating an S3 bucket, there's a **create** button on the bottom left corner, this is what reinvent is all about folks! At the moment, you have to use a Lambda to 'subscribe' Kineses to SNS, but my new buddy at AWS is going to upvote it on roadmaps to add Kinesis to the list of direct SNS subscriptions. For the remainder of the workshop, I had no idea what I was doing, but my graphs looked very promising.
> I have no idea wtf I'm doing, but it looks nice. The trained model is stored in S3, a service I do understand (a bit). - Rob, 2019

At the end of the session, a leaderboard was created to rank all the best models. I'm very proud that I made the top 50, Kenneth was only a couple places before me. This is due to the fact that he had some idea of what he was doing and he is better at reading documention. 

{% asset_img leaderboard.jpg "Leaderboard of best models with SageMaker" %}

<!-- Some people don't read comments and then fail horribly, like me. 
I have no idea what I'm doing, but things look promising. -->

<!-- Do automated training based on a CW alarm that triggers a lambda that triggers retraining. -->