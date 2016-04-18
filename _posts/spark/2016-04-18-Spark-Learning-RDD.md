---
layout: post
title: Spark Learning RDD
category: Scala
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

#### .map()  

```
rdd.map(_ * 3)
```  

#### .flatMap()  

```
rdd.flatMap(_.split(" "))
```  


