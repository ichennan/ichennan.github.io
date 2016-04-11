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

## Nothing用法  

{% highlight scala %}  

def error(msg:String): Nothing = throw new RuntimeException(msg)

def divide(x:Int, y:Int):Int = if(y!=0) x/y else error("divided by zero")
// as Nothing is the subClass of all class, so it's the subClass of Int, so the type of divide is still Int
{% endlight %} 

# Any有两个子类 AnyVal 和 AnyRef  

## AnyVal : 内建值类型的父类  

