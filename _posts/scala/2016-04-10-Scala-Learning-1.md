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
{% endhighlight %}  

# Any有两个子类 AnyVal 和 AnyRef  

## AnyVal : 内建值类型的父类  

`Byte` , `Short` , `Char` , `Int` , `Long` , `Float` , `Double` , `Boolean` , `Unit`  
这些类的实例都写成字面量  
值类型被定义为既是 `抽象` 的, 又是 `final` 的, 不能 `new` 创造实例  
`Unit` 类似 `void` , 只有一个实例值 `()`  

值类型的 `==` `equals` 就是 `自然值` 相等

## AnyRef : 所有引用类的基类, 类似Object  

所有 `AnyRef` 都有子类 `Null`  
`Null` 和值类型不兼容  

### String  

{% highlight scala %}
val x = "abc"
val y = new String("abc")
{% endhighlight %}  

由于 `==` 与 `equals` 等价, 所有 `==` 和 `euqals` 都是判断 `String` 自然值相等( `java` 里 `==` 判断引用相等, `equals` 判断自然值相等)  
判断 `String` 的引用是否相等 要用 `eq` `ne`  

待续  

![1](/public/img/2016-04-10-Scala-Learning-1-1.png)  

严重参考 [http://www.imobilebbs.com/wordpress/archives/4938](http://www.imobilebbs.com/wordpress/archives/4938)

