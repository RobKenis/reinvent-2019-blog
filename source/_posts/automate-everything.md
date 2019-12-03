---
title: Automate everything
cover_index: 2019/12/DAY/TITLE/index.jpg
tile_color: '#fea832'
date: 2019-12-03 09:35:50
tags:
---
{% asset_img banner.png "Description goes here" %}

# Notes
- Why is this dude talking about separating builders and ops ?

# Why automate ?
- Build fast, fail fast. Manual steps are mad slow.

# What to automate ?
## Enable
> It's always a day one
> A new team, a new workload, a new developer...
- Enable landing zone on day 1
- Structure account layout (probably multiple accounts)
    - Create orginazations
    - Setup network infrastructure
- Make setting up accounts easier with Control Tower. This thing simplifies 'day one'
    - Setup landing zone
    - Setup SSO
    - Establish guardrails, best practices
    - Automate compliant account provisioning
    - Control Tower offers dashboards aboout *compliant* resources
## Provision
- CloudFormation all the things!
- Use stack sets to setup stack across multiple accounts and regions
- Enable self-service with Service Catalog
### Automate governance at scale
- Setup Service Catalog in hub account, share portfolio across underlying accounts
    - This gives admins governance about resources and developers the speed to use the resources
## Operate
- Monitor resources and workloads
- Audit resource configurations and policies
- Use trusted advisor

# How to share Service Catalog across accounts
- Create Stack in hub account. Notify underlying account of stack, send them a presigned url for the stack template for example
- Create a stack in the underlying account from the presigned url. Create a portfolio in the sub-account. No idea how this dude did it tho..

# How GoDaddy did it
- Automate landing zone
    - Define vpc
    - Enable monitoring streams for operational perspective
- Service Catalog
    - One portfolio didn't fit all, so divide in 4 portolios
        - Containers, serverless, monitoring and a fourth one
    - Only provide relevant portfolios for teams to reduce noise
    - Use guardrails like template constraints so teams can't deploy a GPU ec2 instance by accident
- CloudFormation
    - Standardized vpc configuration
    - Streamline deverloper and operational experience
- Systems Manager
    - Configuraion-driven deployments using Parameter Store
    - Remove ssh ingress to all production instances. Allow terminal access using Session Manager 
        > This looks promising
- Node rotations
    - Remove the need to patch
    - Golden AMI pipeline bakes the perfect ami. AMI id is set in parameter store that are referenced by CloudFormation
    - If new ami is created, stacks are updated with new SSM reference so nodes are updated

# The GoDaddy developer experience
- Simplify the onboarding on AWS
