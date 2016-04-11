---
layout: post
title: Play Framework Installation
category: Play
tags: play_framework installation
keywords:
description:
---
听说 `palyFramework` 是 `scala` 里比较流行的框架, 所以想弄过来学习一下  
然后发现它和 `Activator` 是捆绑在一起的, 这两个似乎都是 `typesafe` 公司的产品  
所谓 `typesafe` 也就是 `sbt` 的开发商, 现在似乎改名叫 `Lightbend` 了  
总之目前这个公司似乎成了 `scala` 的官网了, 有点像 `Oracle` 至于 `java`  
但是这货说它改名的原因是因为不想让别人以为他们的产品只有 `scala` , 因为他们的很多客户在用着 `java`  
突然觉得 `scala` 前途飘渺

总之下载了 `Offline Distribution` (版本 `Play-2.5.1` , `Activator-1.3.9` , 大小 `640M` )  
解压生成 `activator-dist-1.3.9` 文件夹, 我把 `activator-dist-1.3.9/bin` 加到 `PATH` 里  
然后再终端输入  

```
$ activator new myFirstActivator
```  

它会提示用那种模块, 我选了  

> 6 Play with Scala  

接着就会自动创建了 `myFirstActivator` 的文件夹, `cd myFirstActivator` 进入文件夹后  

```
$ activator run
```  

之后就是漫长的下载各种东西  
之后在[http://localhost:9000/](http://localhost:9000/)就可以看到页面了  


