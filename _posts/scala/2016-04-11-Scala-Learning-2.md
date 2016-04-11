---
layout: post
title: Scala Learning - 2
category: Scala
tags: scala trait
keywords:
description:
---
## Trait  

继承 `类` , 遵循 `接口` , 混合 `特性`  

```
extends ClassA
impletends InterfaceA
extends TraitA with TraitB with TraitC
```

`scala` 中没有接口 `interface` , 没有关键词 `implements`  

`trait` 相当于综合了 `interface` 和 `abstract class`  
相比于 `interface` , 它的方法可以具体实现  
相比于 `abstract class` , 一个 `类` 可以混合多个 `trait`  

{% highlight scala %}
trait TraitA{
  def functionA
}
trait TraitB{
  def functionB = println("B")
}
trait TraitC1{
  def functionC = println("C1")
}
trait TraitC2{
  def functionC
}

class ClassZ extends TraitA with TraitB with TraitC1 with TraitC2{
  def functionA = println("A")
  override def functionC = println("C from Z")
}

object Abc extends App{
  val z = new ClassZ
  z.functionA
  z.functionB
  z.functionC
  val za:TraitA = z
  val zb:TraitB = z
  val zc:TraitC1 = z
  za.functionA
  zb.functionB
  zc.functionC
}
{% endhighlight %}  

结果  

```
A
B
C from Z
A
B
C from Z
```