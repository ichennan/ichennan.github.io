---
layout: post
title: Scala Learning - 1
category: Scala
tags: scala
keywords:
description:
---
## Any  

所有的类都继承自Any  
所有的类都有子类Nothing  
所有的类都有 == != equals hashcode toString  
其中 == 和 != 定位为final, 不可以被重载  
由于 == 与 equals等价, 所以可以通过重载equals修改 == 和 != 的定义  

## Any有两个子类 AnyVal 和 AnyRef  

### AnyVal : 内建值类型的父类  

Byte, Short, Char, Int, Long, Float, Double, Boolean, Unit  
这些类的实例都写成字面量  
值类型被定义为既是抽象的, 又是final的, 不能new创造实例  
Unit类似void, 只有一个实例值()  

### AnyRef : 所有引用类的基类, 类似Object  

待续


