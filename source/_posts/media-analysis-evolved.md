---
title: Media Analysis Evolved Workshop
cover_index: 2019/12/02/media-analysis-evolved/bezos.jpg
tile_color: '#8499e7'
date: 2019-12-02 23:02:03
tags:
---
{% asset_img architecture.png "Media Insights Engine architecture" %}

## Media Insights Engine (MIE)

MIE is a serverless framework to accelerate the development of applications that discover next-generation insights in your video, audio, text and image resources by utilizing AWS Machine Learning services. The engine enables developers to:

- Create media analysis workflows from a library of base operations built on AWS Machine Learning and Media Services such as Amazon Rekognition, Amazon Transcribe, Amazon Translate, Amazon Cognito, Amazon Polly, and AWS Elemental MediaConvert.
- Execute workflows and store the resulting media and analysis for later use.
- Query analysis extracted from media.
- Interactively explore some of the capabilities of MIE using the included content and analysis and search web application.
- Extend MIE for new applications by adding custom operators and custom data stores.

## Components

### Control Plane
Executes the AWS Step Functions state machine for the workflow against the provided input. Workflow state machines are generated from MIE operators. As operators within the state machine are executed, the interact with the MIE data plane to store and retrieve derived asset and metadata generated from the workflow.

### Data Plane
Stores metadata for an asset that can be retrieved as a single block or pages of data using the objects AssetId and Metadata type. Writing data to the pipeline triggers a copy of the data to be stored in a Kinesis Stream.

### User Interface

MIE comes with a web based interface to upload media, run content analysis workflows and view extracted metadata from their media files.

{% asset_img detection.jpg "Detected objects in video" %}

## Read more

You can find more information about Media Insights Engine [here](https://github.com/awslabs/aws-media-insights-engine).
