---
layout: post
title: DesignPattern-2
category: Java
tags: java designPattern
keywords:
description:
---

撸个出现频率最多的单例模式  
  
[ichennan.com 有空来逛逛](<http://ichennan.com>)  

## 单例模式 Singleton  

> 一个类有且仅有一个实例，并且自行实例化向整个系统提供  
> 1. 一个类只有一个实例  
> 2. 自己创建这个实例  
> 3. 整个系统都使用这个实例  
  
这个模式直接看代码，比看定义容易理解。Talk is cheap, show me the code.  

### 饿汉

```
public class Singleton {  
    private static Singleton instance = new Singleton();  
    private Singleton (){}  
    public static Singleton getInstance() {  
        return instance;  
    }  
}  
  
或者  

public class Singleton {  
    private static Singleton instance;
    static{
        instance = new Singleton();
    }   
    private Singleton (){}  
    public static Singleton getInstance() {  
        return instance;  
    }  
}  
```
> 优点: 写法简单，类加载的时候完成实例化，避免线程同步问题  
> 缺点: 没有实现lazy loading，加载时候就实例化了。造成内存浪费  

### 懒汉  

```
public class Singleton {  
    private static Singleton instance;  
    private Singleton (){}  
  
    public static synchronized Singleton getInstance() {  
// 若无synchronized，则线程不安全  
        if (instance == null) {  
            instance = new Singleton();  
        }  
        return instance;  
    }  
}  
```

> 优点: lazy loading  
> 缺点: 效率低，每次获得实例，执行getInstance()都需要同步  

### 懒汉-双重锁定  
  
与懒汉的区别在于，不是同步getInstance()方法，而是在判断为null的时候，同步Singleton.class  
同时用了volatile，避免了instance在分配内存和初始化之间的多线程问题，所以称之为双重锁定  

```
public class Singleton {  
    private volatile static Singleton instance;  
    private Singleton (){}  
    public static Singleton getInstance() {  
        if (instance == null) {  
            synchronized (Singleton.class) {  
                if (instance == null) {  
                    instance = new Singleton();  
                }  
            }  
        }  
    return instance;  
    }  
}  
```

> 优点: 线程安全，延时加载，效率较高  

### 静态内部类

```
public class Singleton {  
    private static class SingletonHolder {  
        private static final Singleton INSTANCE = new Singleton();  
    }  
    private Singleton (){}  
    public static Singleton getInstance() {  
        return SingletonHolder.INSTANCE;  
    }  
}  
```

### 枚举  

```
enum Singleton{  
    INSTANCE;  
}  
```
  
  
  
## 防漏洞  
  
### 防止反射漏洞  

在构造函数里抛出异常

```
private Singleton() {  
    if (null != instance) {  
        throw new RuntimeException();  
    }  
}  
```

### 防止反序列化漏洞  
  
```
private Object readResolve() throws ObjectStreamException {  
    return instance;  
}  
```


