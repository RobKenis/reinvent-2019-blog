---
title: Automate everything
# cover_index: 2019/12/DAY/TITLE/index.jpg
tile_color: '#fea832'
date: 2019-12-02 22:30:50
tags:
---
Automating is key, wether you are provisioning your infrastructure or deploying your application. Save yourself the hassle of clicking in the AWS console for hours and hours. In this session, the benefits of [CloudFormation](https://aws.amazon.com/cloudformation/) and [Service Catalog](https://aws.amazon.com/servicecatalog/) are pointed out once again.

## Why automate?
Build fast, fail fast. Manual steps are mad slow.

## What to automate?
### Enable
> It's always a day one. A new team, a new workload, a new developer...

Make the process of adopting a new accounts simpler and quicker by following these steps:
- Enable [Landing zone](https://aws.amazon.com/solutions/aws-landing-zone/) on day 1
<!-- - Structure account layout (probably multiple accounts)
    - Create orginazations
    - Setup network infrastructure -->
- Structure your account early on, as you will probably create multiple in the long run. Set up the required Organizations and start planning out your network infracstructure.
- Make setting up accounts easier with [Control Tower](https://aws.amazon.com/controltower/). This thing simplifies 'day one' by setting up Landing zone, Single Sign-On and establishing guardrails. It defines how you want your teams to define and use resources. Prohibit the use of public S3 buckets or load balancers without *https* for example. Control Tower creates dashboards about the resources provisioned in the accounts, so you can spot the nasty ones and blame the developers that created them. *look away scrum masters*

### Provision
CloudFormation all the things! Use stack sets to setup stack across multiple accounts and regions. If you stumble upon a stack that could be useful for other people, make it available in Service Catalog.
#### Automate governance at scale
Setup Service Catalog in hub account, share a portfolio across the underlying accounts. This gives admins governance about resources and developers the speed to use the resources.

### Operate
Monitor resources and workloads using Cloudwatch, audit resources configuration with [AWS Config](https://aws.amazon.com/config/) and use the [Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) to get the hottest tips and tricks to improve your AWS account.

## How GoDaddy did it
- Automate Landing zone creation and network setup. Enable automatic log streaming to central account to streamline operational tasks.
- Service Catalog
    - One portfolio didn't fit all, so divide in 4 portolios *(Containers, serverless, monitoring and a fourth one)*
    - Only provide relevant portfolios for teams to reduce noise
    - Use guardrails like template constraints so teams can't deploy a GPU ec2 instance by accident
- Systems Manager
    - Configuration-driven deployments using Parameter Store
    - Remove ssh ingress to all production instances. Allow terminal access using Session Manager
- Node rotations
    - Remove the need to patch
    - Golden AMI pipeline bakes the perfect ami. AMI id is set in parameter store that are referenced by CloudFormation
    - If a new ami is created, stacks are updated with new SSM reference so nodes are updated

{% asset_img theatre.jpg "Venetian theatre" %}
