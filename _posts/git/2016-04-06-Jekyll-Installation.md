---
layout: post
title: Jekyll Installation
category: Git
tags: jekyll installation
keywords:
description:
---
哎, 装个 `Jekyll` 都花了快一个下午. 不过也算是在学习 `Linux` 了, `ruby` 啊 `gem` 之类的

`Jekyll` 是通过 `gem` 安装的, 而大概 `gem` 是 `ruby` 下面的, 所以我们需要安装 `ruby`  
而 `yum` 下直接安装的 `ruby` 版本太低, 所以我们需要一个叫 `rvm` 的 `ruby` 版本管理工具去安装 `ruby` 

**yum安装ruby**  

```
$ yum install -y ruby
$ yum install -y ruby-devel ruby-docs ruby-ri ruby-rdoc
$ yum install -y rubygems
```  

如果这时候你尝试去安装 `jekyll` , 你会发现它说版本太低之类的, 所以你要开始手动之旅了  
但是你也不能省略这个步骤, 因为有些时候需要用到这个低版本的 `gem`  

**安装rvm**  

```
$ yun install -gcc
$ curl -sSL https://get.rvm.io | bash -s stable
```  

这个时候会提示签名失败之类的  

![1](/public/img/2016-04-06-Jekyll-Installation-1.png)  

你就按它提示的输入  

```
$ gpg2 --keyserver hkp://keys.gnupg.net --recv-keys ***后面的字符串***
```  

之后你再走这条命令就ok了  

```
$ curl -sSL https://get.rvm.io | bash -s stable
```  

接着  

```
$ source /etc/profile.d/rvm.sh
```  

至此, `rvm` 安装成功, 可以用 `rvm -v` 测试一下  
接着安装 `ruby` , 你可以指定版本, `Jekyll` 最低要求 `2.0.0` , 所以我就装了 `2.0.0`  

**安装ruby**  

```
$ rvm install ruby 2.0.0
$ rvm list
$ rvm use 2.0.0 --default
```

`list` 是列出本机所有 `ruby` 版本, `use` 是使用版本, `default` 是更改默认版本, 不然有可能重启后又用了低版本

**安装Jekyll**  

```
$ gem install jekyll
```  

**使用Jekyll**

`Jekyll` 的具体使用需要开过一篇来说, 目前我也只是用了别人的模板, 所以没有深入的学习  
这边说下简单的创建和使用  

```
$ jekyll new myFirstJekyll
```  

这样就创建好了, 进入到 `myFirstJekyll` 文件夹, 然后启动服务, 就可以了  

```
$ cd myFirstJekyll
$ jekyll serve
```  

然后你用浏览器输入 [http://localhost:4000](http://localhost:4000) 就可以看到网站了