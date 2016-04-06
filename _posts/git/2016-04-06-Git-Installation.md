---
layout: post
title: Git Installation
category: Git
tags: Git Installation
keywords:
description:
---
终于开始和linux打交道了, 开始学习spark, 准备把学习过程中的项目都放到github上, 再用github pages记录一下学习过程  
看到github pages默认是用jekyll, 以为只有linux下才能使用, 折腾了一天弄好了, 发现没有必要, 在Win或Mac下也可以, 反正github上有引擎, 自己只要负责写txt就好了  
所以最后在linux, Win, Mac下都安装了Git, 开始接触vim, 然后学习了一下Markdown  

##Linux安装Git(CentOS)  

用的CentOS6, 如果直接用yum安装, 它会显示版本, 如果是1.7.x的话, 你就按N, 退出安装, 不然装了待会还得屏蔽这个低版本  
`yum install` 和 `yum -y install` 区别就是 `-y` 就是省掉中间的确认步骤, 如果你不确定版本是否合适, 就别加上 `-y`  

```
yum install git
```

ok, 如果你用的是CentOS7或以上, 它提示的版本是2.0.0+ 的话, 你确认安装, 应该就可以了  
如果提示版本是1.7, 那么和我一样, 开始手动安装  

**安装依赖软件**  
```
yum -y install zlib-devel openssl-devel perl cpio expat-devel gettext-devel
yum install curl-devel
yum install autoconf
```
**下载Git**  
```
mkdir /app/git
cd /app/git
wget http://codemonkey.org.uk/projects/git-snapshots/git/git-latest.tar.xz
```
**解压Git**  
```
xz -d git-latest.tar.xz
tar -xvf git-latest.tar
```
**安装Git**(git-2016-04-01这个是你解压git的生成的文件)  
```
autoconf
./configure --prefix=/app/git/git-2016-04-01
make
make install
```
**配置环境变量**  
```
vim /etc/profile
```
**在文本最后添加上**  
```
export GIT_HOME=/app/git/git-2016-04-01
export PATH=$GIT_HOME:$PATH
```
**使环境变量生效**  
```
source /etc/profile
```
**ok, 大功告成, 亲个嘴吧**  
```
git --version
```