---
layout: post
title: Java Learning-2
category: Java
tags: java
keywords:
description:
---

## Java反射机制  
  
编译，加载，连接，初始化  

> 编译: 生成类文件，也就是.class文件  

> 加载  
> 1. 将类文件中的二进制数据读入内存  
> 2. 并将其放在运行时数据区的方法区内  
> 3. 然后在堆区创建一个Java.lang.Class对象，用来封装类在方法区的数据结构  
>    *该Java.lang.Class对象是单实例的，即无论这个类创建多少对象，它的Class对象是唯一的*  
>    *获得该Class对象的方法有*  
> 1. Class.forName("com.eth.Student"): 加载并初始化  
> 2. Student.Class: 装入内存，不初始化  
> 3. student.getClass()  

> 连接  
> 1. 验证: 确保被加载的类的正确性  
> 2. 准备: 为类的`静态变量`分配内存，并将其初始化为默认值  
> 3. 解析: 把类中的`符号引用`转换为`直接引用`  

> 初始化: 为类的`静态变量`赋予正确的初始值  


## 类加载时机  
  
类的初始化时机正是java程序对类的首次主动使用:  

> 1. 生成类对象的时候，会加载该类及该类所有父类  
> 2. 访问该类的静态成员的时候(类或接口的静态变量或类的静态方法)  
> 3. 反射(Class.forName等)  
> 4. 被标明为启动类的类在JVM启动时(e.g. JavaTest)  

ClassLoader类的loadClass方法加载一个类，并不是对类的主动使用，不会导致类的初始化  

接口有静态变量时，可以被初始化。初始化接口时不会初始化其父接口。初始化类时不会初始化其接口。

```
Student s = new Student();  
相同于  
Student s = (Student)Class.forName("com.eth.Student").newInstant();  
相同于  
Student s = Student.class.newInstant();  
相同于  
Student ss = s.getClass().newInstant();  
相同于  
Class c = Class.forName("com.eth.Student");  
Student s = (Student)c.newInstant();  
```
  
也就是分为两步，先加载类，后实例化  
  
> newInstant(): 弱类型。低效率。只能调用无参构造函数  
> new: 强类型。相对高效。各种public构造  

## 静态方法，静态代码块

好像没有什么官方的定义，来吧，show you the code  
此处加载为广义的加载(编译，加载，连接，初始化)  
  
```
Class Student{
    static String s1 = "hello";
    String s2 = "goodbye";
    public static void f1(){
        System.out.println("f1 f1 f1");
    }
    {
        System.out.println("f2 f2 f2");
    }
    static{
        System.out.println("f3 f3 f3");
    }
    public void f4(){
        System.out.println("f4 f4 f4");
    }
}
```  
  
f1就是静态方法咯, f3就是静态代码块。  

静态变量s1 和 静态代码块f3 在加载的时候执行。  
非静态变量s2 和 非静态代码f2 在加载 和 每次实例化 都会执行。  
如果有父类，那总体顺序就是  
  
> 父f1 -> f1 -> (父f2 -> 父构造 -> f2 -> 构造) * n  
  
f1, f4就是方法啦，有人调用才能执行。  
  
> 静态方法f1: 可以用类名直接调用，不需要创建对象/实例化。  
> 只能调用同类中的静态成员(静态变量，静态方法)。  
> 不能以任何方式引用this或super关键字。  

## 四个规则  

> 1. 初始化构造时，先父后子；只有在父类所有都构造完后子类才被初始化  
> 2. 类加载先是静态、后非静态、最后是构造函数  
>    *静态构造块、静态类属性按出现在类定义里面的先后顺序初始化，同理非静态的也是一样的*  
>    *只是静态的只在加载字节码是执行一次，不管你new多少次，非静态会在new多少次就执行多少次*  
> 3. java中的类只有在被用到的时候才会被加载  
> 4. java类只有在类字节码被加载后才可以被构造成对象实例  