---
layout: post
title: Git Installation
category: Git
tags: git installation
keywords:
description:
---
终于开始和 `linux` 打交道了, 开始学习 `spark` , 准备把学习过程中的项目都放到 `github` 上, 再用 `github pages` 记录一下学习过程  
看到 `github pages` 默认是用 `jekyll` , 以为只有 `linux` 下才能使用, 折腾了一天弄好了  
发现没有必要, 在 `Win` 或 `Mac` 下也可以, 反正 `github` 上有引擎会自动解析成网页
我们只要下载好模板到项目, 然后负责写文档提交就行了  
所以最后在 `linux` , `Win` , `Mac` 下都安装了 `Git` , 开始接触 `vim` , 然后学习了一下 `Markdown`  

## Linux安装Git(CentOS)  

用的 `CentOS6` , 如果直接用 `yum` 安装, 它会显示版本, 如果是 `1.7.x` 的话, 你就按 `N` , 退出安装, 不然装了待会还得屏蔽这个低版本  
`yum install` 和 `yum -y install` 区别就是 `-y` 就是省掉中间的确认步骤, 如果你不确定版本是否合适, 就别加上 `-y`  

```
$ yum install git
```  

ok, 如果你用的是 `CentOS7` 或以上, 它提示的版本是 `2.0.0+` 的话, 你确认安装, 应该就可以了  
如果提示版本是 `1.7.x` , 那么和我一样, 开始手动安装  

**安装依赖软件**  

```
$ yum -y install zlib-devel openssl-devel perl cpio expat-devel gettext-devel
$ yum install curl-devel
$ yum install autoconf
```  

**下载Git**  

```
$ mkdir /app/git
$ cd /app/git
$ wget http://codemonkey.org.uk/projects/git-snapshots/git/git-latest.tar.xz
```  

**解压Git**  

```  
$ xz -d git-latest.tar.xz
$ tar -xvf git-latest.tar
```  

**安装Git**(git-2016-04-01这个是你解压git的生成的文件)  

```  
$ autoconf
$ ./configure --prefix=/app/git/git-2016-04-01
$ make
$ make install
```  

**配置环境变量**  

```
$ vim /etc/profile
```  

**在文本最后添加上**  

```
$ export GIT_HOME=/app/git/git-2016-04-01
$ export PATH=$GIT_HOME:$PATH
```  

**使环境变量生效**  

```
$ source /etc/profile
```  

**ok, 大功告成, 亲个嘴吧**  

```
$ git --version
```  

## Mac安装Git  

嗯, 这个可难了, 下载一个叫 `git-2.6.4-intel-universal-mavericks.dmg` 的文件, 安装就ok了  
网址 [https://git-scm.com/download/mac](https://git-scm.com/download/mac)  
这个安装完似乎啥都不做, 直接终端输入 `git --version` 已经可以了  

## Win安装Git  

人们说 `Win` 下 `Git` 的软件有很多, 嗯， 反正我用的和 `Mac` 上的一样的  
[https://git-scm.com/download/win](https://git-scm.com/download/win)  
安装完后再在所有程序里会有个 `Git` 文件夹, 点开其中的 `Git Bash` 就到 `Git` 的终端了  
顺带说一句, 这个 `Git` 除了 `Git` 的命令外, 还可以用 `Vim`  

目前在 `Win` 下, 我还有用 `Intellij` 的 `git` 配合使用, 不过习惯了 `Git Bash` 之后似乎觉得没有必要了