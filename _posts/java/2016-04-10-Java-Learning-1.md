---
layout: post
title: Java Learning - 1
category: Java
tags: java
keywords:
description:
---
## 抽象方法  

只有申明, 没有具体的实现, 必须用 `abstract` 修饰  

```
abstract void fun()
```  

## 抽象类  

如果 `类` 含有 `抽象方法` , 就是 `抽象类` , 也必须用 `abstract` 修饰  
当然, `抽象类` 也可以不包含 `抽象方法`  

与 `普通类` 区别  

1. `抽象方法` 必须用 `public` 或 `protected` (因为用 `privated` 无意义)  

2. 不能创建 `对象` (因为有 `抽象方法` -无具体实现的方法)  

3. `子类` 继承 `抽象类` , 必须实现 `抽象方法` , 否则 `子类` 必须也是 `抽象类`  

4. 除此之外与 `普通类` 一样, 可以有 `成员变量` 和普通的 `成员方法`  

## 接口  

可以含有变量和方法  

1. 变量只能是 `public static final` , 且一般不定义变量  

2. 方法只能是 `public abstract` 的 `抽象方法` , 不能具体实现  

3. `普通类` 遵循 `接口` , 必须实现 `接口` 中所有方法, `抽象类` 遵循接口, 可不实现  

## 抽象类与接口区别  

### 语法层面  

1. `接口` 只能有 `抽象方法` , `抽象类` 可以有 `成员方法` 的实现细节  

2. `接口` 的变量只能是 `public static final` , `抽象类` 的变量可以是各种类型  

3. `抽象类` 中可以有 `静态代码块` 和 `静态方法` , `接口` 中不能有  

4. 一个 `类` 只能继承一个 `抽象类` , 但可遵循多个 `接口`  

### 设计层面  

1. `抽象类` 是对一种事物的抽象, 即对 `类` 的抽象(整体: 包括属性和行为), `接口` 是对行为的抽象  

2. `抽象类` 是一种 `是不是` 的关系( `子是父种类` ), 接口是 `有没有` 的关系( `子有父功能` )  

3. `抽象类` 是 `模板式设计` , `接口` 是 `辐射式设计`  

> Airplane, Bird 可以设计为抽象类, Airplane可以生成波音, 空客, Bird可以生成翠鸟, 燕子  
> 而Fly可以设计为接口  

> 模板即ppt模板, 模板A设计了B和C, 改动模板A, 会自动更改B和C, 也就是抽象类中直接更改, 子类不需要变更  
> 接口如果变更, 所有遵循这个接口的类都必须变更  

> 门和警报, 门都有open()和close(), 有些门具有警报alarm(), 可以这样设计  

{% highlight java %}
abstract class Door{
    void open();
    void close();
}

interface Alarm{
    void alram();
}

class AlarmDoor extends Door implements Alarm{
    void open(){
        //...
    }
    void close(){
        //...
    }
    void alram(){
        //...
    }
}
{% endhighlight %}  


严重参考 [http://www.cnblogs.com/dolphin0520/p/3811437.html](http://www.cnblogs.com/dolphin0520/p/3811437.html)