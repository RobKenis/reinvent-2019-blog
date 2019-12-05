---
title: Keynote wiht Werner Vogels
cover_index: 2019/12/05/keynote-with-werner-vogels/index.jpg
tile_color: '#fea832'
date: 2019-12-05 08:18:36
tags:
---
{% asset_img banner.png "Keynote with Werner Vogels" %}

> There's no compression algorithm for experience - Werner Vogels' T-Shirt team, 2019

The experience we've built over the last 13 years learned us alot.

> Sometimes innovation is about focussing on the things that will never change for your customers - Jeff Bezos

## Virtualization
The bread and butter of the compute parts from day one. Classical virtualization has been around for a long time. x86 has come to life by major research at Stanford. We really pushed boundaries of virt over time. All guest OS's are fighting for the host resources, especially for network. Guests would see network jitter because they're fighting for the same network. AWS Nitro reinvented the virtualization to solve these problems, and reduce virt overhead.  Amazon took the lessons they learned in software and applied them to hardware. 
Microservices are the small bilding blocks that you can quickly improve on. Can we create a world where hardware is built like that. 

### AWS Nitro System
Step 1: Move the network component to a seperate card, the first thing they did in 2016. It took another 2 years to learn what happens when you offload components to a second card.
Step 2: Move ebs processing to a separate card.
Step 3: Offload all I/O to separate cards
Step  4: Move the management components to Nitro controller

#### Nitro volume attach
An EBS volume attachement talks to the Nitro controller, which then talks to the OS level controller. The pre-nitro hypervisor introduces way more jitter. The nitro hypervisor increased IOPS tremendously, the bandwitch increased fron 14Gb/s to 19Gb/s. 

C5 instances have performance close to bare metal, this is because the hypervisor layer is so thin. Network optimized instances improved network throughput 4x. 

#### Kill Dom0
Do not trust the thing. You could do a memory dumpm which is a massive security risk. By removing Dom0, you can remove ssh which is way more secure. 

## Passie communications design
The nitro ctonroller talks to the hypervisor, not the other way around. The external control plane can talk to the nitro controller, but not the other way around. When the communication happens the other way around, your system is compromised. Inside the nitro controller, all components can talk to eachother. With nitro, everything is encrypted by default with no performance loss. Don't even trust your guests, make sure they can not do anything with the hardware. Thay may not change volatile memory. 

### Nitro: the base for innovation
Live updates from the micro part without anything taken down. Start running bare metal and create outposts. This is all enabled by Nitro which controls the environmtns. 

### Protect sensitive data
Nitro enclanve **NEW** constantly checks if code is not compromised. Customers want control over sensitive data. Nitro changes the way we think about your compute environment.

## Firecracker
### Fargate
Serverless compute for containers. Security is number one priority. In fargate, each copy of an application runs in its own machine under the hood in fargate, isolated from other machines in fargate. This ensures isolation at multiple levels. 
When a traffic spike comes in, Kubernetes takes a while to spin up more instances introducing latency. This is called underprovisioning. Fargate allocates the right amount of compute per pod, only inducing latency when pods are spinning up. Dont worry about underprovisioning and overprovisioning. Fargate reacts quicker to changes in traffic and allocates the right amount of conpute per pod. 
Each application had its own Fargate control plane. A traditional vm will reserve 4MB for graphics, containers dont usually have graphics, so this is waste. Fargate is purpose built for containers using microVMs. These are fast and lightweight and only have devices they actually need. A microVM requires only 5MB of overhead in total. Each application can use a separate microVM instead of a separate EC2 instance. Originally, the Fargate data plan ran on every vm. The new control plane is designed to run directly on bare metal, making the microVMs faster to startup. [Firecracker containerd](https://firecracker-microvm.github.io) looks cool. 

### Lambda
Lambda runs on firecracker. The rapid adoption of serverless is happening in the enterprise. It's cheaper and easier. 

#### Vanguard