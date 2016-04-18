---
layout: post
title: Spark Learning
category: Spark
tags: spark
keywords:
description:
---
## Spark运行模式  

#### local  

本地模式, 可分为local单线程和local-cluster多线程  

#### standalone  

Master/Salve 支持zookeeper实现HA  

#### on yarn  

yarn负责资源管理, spark负责任务调度和计算  

#### on mesos  

mesos负责资源管理, spark负责任务调度和计算  

#### on cloud  

比如AWS的EC2