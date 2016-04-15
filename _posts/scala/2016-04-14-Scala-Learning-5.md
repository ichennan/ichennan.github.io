---
layout: post
title: Scala Learning - 5
category: Scala
tags: scala
keywords:
description:
---
## Extractor  

> 把原文aa@cc.com带入匹配项EMail的unapply方法的参数str, 如果返回None则不匹配, 否则匹配

```
object EMail {
    def unapply(str:String) :Option[(String,String)] ={
        println("i am unapply")
        val parts = str split "@"
        if(parts.length==2) Some(parts(0),parts(1)) else None
    }
}

"aa@cc.com" match{
    case Email(u) => println("user is " + u)
    case _ => println("error")
}

i am unapply
user is aa mail is cc.com
```  
