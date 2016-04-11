---
layout: post
title: Scala Learning - 1
category: Scala
tags: scala
keywords:
description:
---
# Any  

所有的类都继承自 `Any`  
所有的类都有子类 `Nothing`  
所有的类都有 `==` `!=` `equals` `hashcode` `toString`  
其中 `==` 和 `!=` 定位为 `final` , 不可以被重载  
由于 `==` 与 `equals` 等价(由 `equals` 决定 `==` ), 所以可以通过重载 `equals` 修改 `==` 和 `!=` 的定义  

