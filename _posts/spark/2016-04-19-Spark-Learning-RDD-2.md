---
layout: post
title: Spark Learning RDD - 2
category: Spark
tags: spark scala rdd
keywords:
description:
---
1. transformations(lazy)  
2. action  

```
rdd_from_lines.cache()
rdd_from_lines.persist()  
rdd_from_lines.unpersist()  
```  

> 默认级别MEMORY_ONLY  
> MEMORY_ONLY_SER(序列化Java对象)
> MEMORY_AND_DISK
> OFF_HEAP(共享Tachyon内存池, 减少垃圾回收)

## 传递函数到spark  

1. Anonymous Function Syntax匿名函数  
2. 全局单例对象里的静态方法  

## 广播变量 Broadcast variable  

集群所有函数可以访问, 广播之后不能被修改  

```
val broadcastVal = sc.broadcast(Array(1,2,3))  
broadcastVal.value  
>> Array(1,2,3)  
```

## 累加器 Accumulator  

集群可以操作它, 只有驱动程序可以读它的值  

```
val accum = sc.accumulator(3, "Test Accumulator")
accum.value
>> 123
```  

### 自定义累加器  

```
object VectorAccumulatorParam extends AccumulatorParam[Vector] {
    def zero(initialValue: Vector): Vector = {
        Vector.zeros(initialValue.size)
    }

    def addInPlace(v1: Vector, v2: Vector): Vector = {
        v1 += v2
    }
}

// Then, create an Accumulator of this type:
val vecAccum = sc.accumulator(new Vector(...))(VectorAccumulatorParam)
```  






