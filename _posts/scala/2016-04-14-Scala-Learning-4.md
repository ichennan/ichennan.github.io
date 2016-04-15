---
layout: post
title: Scala Learning - 4
category: Scala
tags: scala
keywords:
description:
---

## case class  

1. 会生成一个同名的对象构造器(Factory Method) 省略new创建一个类的实例  
2. 为构造函数的参数创建了属性  
3. 更自然的toString, hashCode, equals, 它们会递归打印, 比较参数属性  

```
scala> println(op)
BinOp(+,Number(1.0),Var(x))
 
scala> op.right == Var("x")
res3: Boolean = true

scala> op.copy(operator="-")
res4: BinOp = BinOp(-,Number(1.0),Var(x))
```  

## pattern matching  

1. _为通配符, 变量比如e, 可以匹配任意的值  
2. no fall through  
3. 没有匹配, 会有MatchError异常  

```
List(0, 2, 4) match{
    case List(0, _*) => yes
}

x match{
    case s:String => ...
    case m:Map[_,_] => ...
}

// 无法区分generic类型
x match{
    case m:Map[Int, Int] => ...
    case m:Map[String, String] => neverHere
}

// 可以区分数组里的generic类型
x match{
    case a:Array[String] =>
    case b:Array[Int] =>
}

```  

匹配后将变量绑定为e  

```
expr match{
    case UnOp("abc", e @ Unop2("ccc", _)) => e
}
```

```
e match{
    case BinOp("+", x, y) if x==y => ...
}
```  

> 一个sealed的类的子类只能在同个文件里定义 sealed abstract class ClassA  

```
// 不提示match warning
(e: @unchecked) match{
    case ...
}
```  

Option类有两个可能值, 一个为Some(x), 一个为None

```
scala> val capitals = Map("France"->"Paris", "Japan"->"Tokyo","China"->"Beijing")

scala> capitals get "France"
res0: Option[String] = Some(Paris)

scala> capitals get "America"
res1: Option[String] = None

scala> def show(x:Option[String]) = x match{
    case Some(s) => s
    case None => "so so so"
}

scala> show (capitals get "America")
res5: String = so so so
```  

```
second.isDefinedAt(List(1,2,3))
```  




