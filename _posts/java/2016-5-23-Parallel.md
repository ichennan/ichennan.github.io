---
layout: post
title: Parallel
category: Java
tags: java parallel
keywords:
description:
---

同步 Synchronous  
异步 Asynchronous  

并发 Concurrency  
并行 Parallelism  

临界区 公共资源 共享资源  

阻塞 Blocking  
非阻塞 Non-Blocking  

死锁 Deadlock  
饥饿 Starvation  
活锁 Livelock  

### 并发级别  

阻塞 Blocking  
无饥饿 Starvation-Free  
无障碍 Obstruction-Free  
无锁 Lock-Free  
无等待 Wait-Free  

### Amdahl定律  

> 加速比 = 优化前系统耗时 / 优化后系统耗时  
> 优化后系统耗时 = 优化前系统耗时 * (串行百分比 + (1 - 串行百分比) / 处理器个数)  
> 加速比 = 1 / (串行百分比 + (1 - 串行百分比) / 处理器个数))  
> 处理器个数无穷大 => 加速比极限为 1 / 串行百分比  

### Gustafson定律  

> 串行百分比为1, 加速比都为1. 串行百分比为0, 加速比都为处理器个数  


