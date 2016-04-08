---
layout: post
title: Github Pages
category: Git
tags: github github-pages
keywords:
description:
---
如果你的账号是 `youraccount`  
你创建一个 `repository` , 名字为 `youraccount.github.io` , 这个就会自动变为你的 `github pages`  
你把 `Jekyll` 项目放到这个文件夹下, 然后你登陆到 [https://youraccount.github.io](https://youraccount.github.io) , 就会直接看见网页了  

`2016/05/01` 开始 `github pages` 不支持 `redcarpet` , 只支持 `kramdown` , 而且 `Jekyll` 说他们默认的引擎也是这个  
那就改为这个呗, 具体语法在这个网址 [http://kramdown.gettalong.org/syntax.html](http://kramdown.gettalong.org/syntax.html)  
目前发现需要更改的地方就是  `#` `##` `###` 后面一定要加空格, 不能直接加文字  

> #一级标题 无法解析  
> # 一级标题 正确  
