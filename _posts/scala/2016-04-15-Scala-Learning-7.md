---
layout: post
title: Scala Learning - 7
category: Scala
tags: scala
keywords:
description:
---

## None  

case object None extends Option[Nothing]
None是Option的子类, 是一个object  

## Null  

final trait Null extends AnyRef  
Null是所有AnyRef的子类, null是Null的唯一对象  

## Nothing  

final trait Nothing extends Nothing  
Nothing是所有类型的子类, 也是Null的子类, 没有对象, 可以用来定义类型, 比如异常的返回类型  

## Nil  

case object Nil extends List[Nothing]  
Nil是一个空的List, 定义为List[Nothing], 是所有List[T]的子类  

## Unil  

abstract final class Unit extends AnyVal  
Unil相当于void, 唯一的实例是(), 当方法不返回任何值的时候使用  

