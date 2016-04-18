---
layout: post
title: Scala Learning - 6
category: Scala
tags: scala
keywords:
description:
---

## Array  
---  

长度固定, 元素可变  

```
val array = new Array[String](3)  
Array(null, null, null)  

val array = Array("a", "b", "c")  
Array.apply("a", "b", "c")  

val array = Array[Any]("a", true, 3)  
val array: Array[Any] = Array("a", true, 3)  
val array: Array[_] = Array("a", true, 3)  

array(0)
```



## List  
---  

长度固定, 元素不可变  

> :: 发音cons  
> ::: 相当于.concat()  

```
val list1 = 4 :: 5 :: 6 :: Nil  
    >> List[Int]=List(1,2,3)  
val list2 = List(1, 2, 3)  
    >> List[Int]=List(1,2,3)  
val list3 = list1 ::: list2
    >> List[Int]=List(4,5,6,1,2,3)
val list4 = list1 :: list2
    >> List[Any]=List(List(4,5,6),1,2,3)
val list5 = list2 ::: Nil
    >> List[Int]=List(1,2,3)
val list6 = list2 :: Nil
    >> List[List[Int]]=List(List(1,2,3))
val list = List.fill(3)(1)
    >> List[Int]=List(1,1,1)
    
list.head
list.tail
list.isEmpty
list.toArray
list.toBuffer
list.toSeq
list.toSet
```

## Tuple  
---  

长度固定, 元素不可变  

> 下标从1开始, 目前最长22  

```
val tuple = (1, ture, "abc")  
tuple._1
```  


## Range  
---  

```
val range = Range(1, 5)
Range(1,2,3,4)
1 to 5
1 until 4

1 to 5 toList
List(1,2,3,4)
Vector(1,2,3,4)
```  


#### package scala.collection  


![collection](/public/img/collection.png)  

#### package scala.collection.immutable  


![immutable](/public/img/immutable.png)  

#### package scala.collection.mutable  


![mutable](/public/img/mutable.png)  



