---
layout: post
title:  "AWS Docker"
date:   2022-05-21 14:07:21 -0600
categories: tech aws fargate
tags: tech aws fargate
author: Trevor Facer
---

## What is Fargate?

[Official Docs](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html)

### Key Ideas

* Allows one to run containers in AWS without managing servers/instances
  * No provisioning/scaling/configuring clusters (aside from ECS Fargate config)
* Runs Amazon Linux 2

## Task Definitions

* Fargate supports a subset of the task definition paramaters available through ECS
* Some paramaters are supported, but have limitations, for example:
  * `volumes` - "Fargate tasks only support bind mount host volumes"

## Network Mode

* Must be set to `awsvpc`, which provides each task with its own ENI

## CPU

* Supports both `ARM` and `X86_64`

| CPU Value    | Memory Value    | Supported OS    |
|---------------- | --------------- | --------------- |
| 256 (.25 vCPU)    | 512 MB, 1 GB, 2 GB | Linux    |
| 512 (.5 vCPU)     | 2 GB, 3 GB, 4 GB | Linux    |
| 1024 (1 vCPU)    | 2 GB, 3 GB, 4 GB, 5 GB, 6 GB, 7 GB, 8 GB | Linux   |
| 2048 (2 vCPU)    | Between 4 GB and 16 GB in 1 GB increments | Linux   |
| 4096 (4 vCPU)   | Between 8 GB and 30 GB in 1 GB increments | Linux   |
