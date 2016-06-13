---
layout: post
title: Transaction
category: Java
tags: java javaEE transaction
keywords:
description:
---

### ACID属性  

> 原子性（atomicity）：事务中的所有动作要么都发生，要么都不发生。  
> 一致性（consistency）：事务将数据库从一种一致状态转变为下一种一致状态。  
> 隔离性（isolation）：一个事务的影响在该事务提交前对其他事务都不可见。  
> 持久性（durability）：事务一旦提交，其结果就是永久性的。  

### 并发问题  

> 脏读（dirty read）：你能读取未提交的数据，也就是脏数据。  
> 不可重复读（nonrepeatable read）：这意味着，如果你在T1时间读取某一行，在T2时间重新读取这一行时，这一行可能已经有所修改。  
> 幻像读（phantom read）：与不可重复读的区别在于：在幻像读中，已经读取的数据不会改变，只是与以前相比，会有更多的数据满足你的查询条件。  

### 隔离级别  

> READ UNCOMMITTED 允许脏读。Oracle没有利用脏读，甚至不允许脏读。  
> READ COMMITTED 只能读取数据库中已经提交的数据。  
> REPEATABLE READ 不仅能给出一致的正确答案，还能避免丢失更新。  
> SEAIALIZABLE 事务在一个环境中操作时，就好像没有别的用户在修改数据库中的数据一样。  

> READ ONLY事务与SERIALIZABLE事务很相似，惟一的区别是READ ONLY事务不允许修改。  

### 丢失

> 第一类丢失更新 A事务在撤销时，“不小心”将B事务已经转入账户的金额给抹去了  
> 第二类丢失更新 A事务在提交时，覆盖B事务已经提交的数据，造成B事务所做操作丢失  

![1](/public/img/2016-06-13-Transaction-1.jpg)  