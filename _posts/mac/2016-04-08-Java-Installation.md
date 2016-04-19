---
layout: post
title: Java8 Installation on Mac
category: Mac
tags: mac java installation
keywords:
description:
---
每次在 `mac` 上弄 `java` 安装都头疼.....  
`Mac` 原先装了 `java7` , 现在需要 `java8` , 在 `Oracle` 下载了 `java1.8.0-77` 的img , next next 之后,  
在 `mac` 的系统设置里 `Java` 版本( `Java` - `Java Control Panel` - `Java` - `View` , 以下简称 `View` )已经是 `8` 了, 而且只有 `8` , 没有 `7`   
但在终端输入 `java -version` , 还是显示 `1.7.x`   
然后网上说的通过这个命令可以看见机器上装了多少个版本的 `java`   

```
$ /usr/libexec/java_home -v
```  

然并卵, 这个命令应该是看 `/Library/Java/JavaVirtualMachines` 这个文件夹下面有多少个 `java` 版本  
而无论我安装了 `java8` 多少遍, 这个文件夹下永远只有 `java7`  
所以不知道是我安装错了, 还是网上的教程千篇一律, 总之 `java1.8.0-77` 安装完之后是不在这个文件夹下的  
而是在我们之前 `View` 里显示的路径, 也就是 `/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home` 这个里面(后面的 `/bin/java` 就不需要了)  
接下来就是在 `~/.bash-profile` 里更改/增加 `JAVA_HOME` 为上面那个路径的, 添加 `JAVA_HOME:bin` 到 `PATH`  
然后 `source ~/.bash-profile` , 理论上再 `java -version` 就可以看到 `8` 了 ... 然!!! 稍后再提

## 卸载JAVA7  

如果你需要卸载原来的 `java7`  
理论上是不需要的, 因为你改了 `PATH` , 每次调用 `java` 这个命令就会调用 `JAVA_HOME` 里的, 但是我恨它, 所以...  
按 `Oracle` 官网上说是这样的  

```
$ sudo rm -fr /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
$ sudo rm -fr /Library/PreferencesPanes/JavaControlPanel.prefpane
```  

第一条命令的话, 你会发现它把所有的 `java` 都删了, 包括 `java7` , `java8`  
所以删完之后, 你再重新安装一遍 `java8` 就可以了  
两条命令完之后, 我自己再跑了一条, 因为我明明记得 `JavaVirtualMachines` 这个下面还有 `java7` , 所以  

```
$ sudo rm -fr /Library/Java/JavaVirtualMachines/1.7.x...
```  

就我所知的, 这样是应该把 `java7` 给弄掉了  

## 路径有空格  

再来说上面说的坑, 就是当我在 `~/.bash-profile` 里设置  

>JAVA_HOME=/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home  

发现文件夹名里有空格, `mac` 识别不了, 这个应该so easy, 转义符或者加引号  
然 !!!  
你有以下三种方式, 假设文件夹名是 `/ab cd/`  

>JAVA_HOME=/ab\ cd/  

>JAVA_HOME="/ab cd/"  

>JAVA_HOME='/ab cd/'  

All work! 然当你在终端输入下面命令的时候，还是会报错  

```
$ $JAVA_HOME
```  

你需要这样输入  

```
$ '$JAVA_HOME'
```

同理, 你的 `$PATH` 也需要变成 `'$PATH'`  
尼玛啊, 有个毛用!!!  
然后听人说, 建立链接, 哇, 一想果然是个好主意  

```
$ ln -sv /ab\ cd /aaa
```  

然而结果是一样的, 它依旧会忠贞的找回最初的路径, 然后报错  
最后...  
我屈服了, 复制 `/ab cd/` 到 `/aaa` , 然后设置 `JAVA_HOME=/aaa` , 世界安宁了...  
`View` 里显示的依旧是 `/ab cd/` 下面的, `PATH` 里调用的 `/aaa` 下面的, 反正一样没区别  

## 愉快  

一个上午就这样愉快的度过了 :)  
尼玛  

# 嗯, 大概在几天后的某个晚上, 我突然想明白了... 当时下载的是jre, 不是jdk... 重新下载安装了jdk, 一切解决...  

# 以上