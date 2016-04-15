---
layout: post
title: Scala Learning - 3
category: Scala
tags: scala
keywords:
description:
---

var age = 0  

{% highlight java %}
private int age;
public int age();
public voide age_=(int);
{% endhighlight %}  

{% highlight scala %}
age
age_=
{% endhighlight %}  

> 这里的age, age_= 就是getter, settter  
> 如果private var age(类私有), 则生成的getter, setter 也变成private的  
> 如果private[this] var age(对象私有), 不会生成getter, setter, 只有当前对象有权限访问age  
> 如果val age, 则只会生成getter, 不会生成setter  

> @BeanProperty var age, 会生成getAge(), age, setAge(int age), age_=(int)  

## 构造函数  

{% highlight scala %}
def Rational(n: Int, b: Int){
    require(b != 0)
}
{% endhighlight %}  

> 每个类都有主构造函数, 主构造函数与类定义在一起  
> 类定义可以有参数, 称为类参数  
> 辅助构造函数的第一个语句都为调用其它构造函数, 最终都会调用主构造函数  

{% highlight scala %}
def f(): Int = try { return 1 } finally { return 2}  
// 返回2  

def f(): Int = try 1 finally 2   
// 返回1  
{% endhighlight %}  

> scala里没有break, continue, 用变量控制, 或者递归实现循环  
> scala支持局部函数,  

{% highlight scala %}
scala> (x: Int) => x + 1
res11: Int => Int = <function1>
{% endhighlight %}  

即类型为带有一个参数的类Function1的一个对象

filter的参数为一个 Any => Boolean 的一个函数 ?  

## 闭包  

原本某个函数A定义为, 有一个参数, 值为一个函数B, 即(Int)Int => Int  

```
def fooA(parameterA: Int) = (parameterB: Int) => parameterB + parameterA  
```  

现定义一个z, 赋值了这个参数, 那么函数B里用到的参数A已经被固定下来了  

```
val z = fooA(100)
```  

所以此时的z为(parameterB: Int) => parameterB + 100  
也就是说当我们赋值100给fooA的时候创建了一个闭包z, 即定义了parameterA的值为100  
之后这个闭包里这个100是无法改变了的, 调用z(333), 即返回433  

> 统一访问原则: Uniform Access Principle  
> 字段变为访问函数, 且访问函数是纯函数(没有副作用且不依赖于可变状态), 对象不需要重写  
> 无参且无副作用, 鼓励省略空括号 如果有副作用, 一定带上括号  
> 成员变量可以重载一个无参函数  

```
def contents: Array[String] = {...}  
val contents: Array[String] = ...  
```  

> 派生意味着子类的值可以用在所有使用父类值得地方  
> final class 不可extends, final def 不可override  








