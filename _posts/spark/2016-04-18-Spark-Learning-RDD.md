---
layout: post
title: Spark Learning RDD
category: Spark
tags: spark scala rdd
keywords:
description:
---

任何数据在Spark中都表示为RDD, 是一种抽象数据类型, 可以看成是一个数组, 但是数据是分区存储的, 所以可以并行处理.

## 创建  

```
val conf = new SparkConf().setAppName("xxx")  
val sc = new SparkContext(conf)  
val rdd_from_file = sc.textFile("README.md")  
val rdd_from_list = sc.parallelize(1 to 100, 3)  
```  

> parallelize(list, x) x为切片数slices, 默认为每一个文件块创建一个切片(slice), 大小为64M  

### .map()  

```
def map[U](f : scala.Function1[T, U]) : org.apache.spark.rdd.RDD[U]
...
rdd.map(_ * 3)
```  

### .flatMap()  

```
def flatMap[U](f : scala.Function1[T, scala.TraversableOnce[U]]) : org.apache.spark.rdd.RDD[U]
...
rdd.flatMap(_.split(" "))
val rdd_from_list = sc.parallelize(1 to 3, 3)  
rdd_from_list.flatMap(x => 1 to x).collect
>> Array(1, 1, 2, 1, 2, 3)
```  


### .mapPartitions()  

分区操作然后合并  

```
def mapPartitions[U](f : scala.Function1[scala.Iterator[T], scala.Iterator[U]], preservesPartitioning : scala.Boolean) : org.apache.spark.rdd.RDD[U]
...
def f[T](inItertor: Itertor[T]) : Itertor[U] = {
    var outItertor = List[U]()
    ...
    outItertor
}
rdd.mapPartitions(f).collect
```

### mapValues  

对key-value值中的value做map  

```
val rdd_from_map = sc.parallelize(List((1, "dog"), (5, "cat"), (2, "fish")), 2)
rdd_from_map.mapValues("this is " + _).collect
>> Array((1, "this is dog"), (5, "this is cat"), (2, "this is fish"))
```

### mapWith() -> mapPartitionsWithIndex()  

第一个函数的参数为partion index(从0开始)  
第二个函数的第一个参数为原元素, 第二个参数为第一个函数的输出  

```
def mapPartitionsWithIndex[U](f : scala.Function2[scala.Int, scala.Iterator[T], scala.Iterator[U]], preservesPartitioning : scala.Boolean) : org.apache.spark.rdd.RDD[U]
...
val rdd = sc.parallelize(1 to 9, 3)  
rdd.mapWith(_ * 10)(a, b => a * 100 + b).collect
>> Array(100, 200, 300, 410, 510, 610, 720, 820, 920)
```  

### reduce  

前两个元素当作参数, 产生新值, 新值与下一个元素再被传入当作参数  

```
sc.parallelize(1 to 6).reduce(_ + _)
>> (((((1 + 2) + 3) + 4) + 5) + 6)
sc.parallelize(1 to 6).reduce(_* 10 + _)
>> ((((1 * 10 + 2) * 10 + 3) * 10 + 4) * 10 + 5) * 10 + 6
```  

### reduceByKey  

对key-value值中的key相同的元素的value进行reduce

```
sc.parallelize(List((1,2),(3,4),(3,6))).reduceByKey(_ + _).collect
>> Array((1,2), (3,10))
sc.parallelize(List(("aaa",2),("bbb",4),("bbb",6))).reduceByKey(_ + _).collect
>> Array(("aaa",2), ("bbb",10))
sc.parallelize("a b c d e f e e e e").flatMap(_.split(" ")).map((_, 1)).reduceByKey(_ + _).collect
>> Array(("a", 1), ("b", 1), ("c", 1), ("d", 1), ("e", 5), ("f", 1))
```  
