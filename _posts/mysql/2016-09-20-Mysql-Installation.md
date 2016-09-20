---
layout: post
title: MySQL Installtion
category: Mysql
tags: mysql
keywords:
description:
---

```
$ rpm -qa | grep mysql  
mysql.abc  

$ rpm -e --nodeps  mysql.abc  

$ whereis mysql  
/usr/local/mysql /usr/lib64/mysql  

$ rm -rf /usr/local/mysql  
$ rm -rf /usr/lib64/mysql  
$ rm -rf /var/lib/mysql
```

download rpm package  
  
mysql5.7.14 :  `http://mirrors.sohu.com/mysql/MySQL-5.7`  
  
centos6 : `mysql-5.7.14-1.el6.x86_64.rpm-bundle.tar`
..

scp to linux  

```
$ scp mysql-community-server-5.7.14-1.el6.x86_64.rpm root@it.com:/etehang
```

第一次尝试 `rpm -ivh mysql-community-server-5.7.14-1.el6.x86_64.rpm`  
  
缺少libaio  
  
```
$ yum install libaio
```

第二次尝试 `rpm -ivh mysql-community-server-5.7.14-1.el6.x86_64.rpm`  
  
缺少libnuma  
  
```
$ yum install libnuma
```

不是啦，你乱讲，是这个  
  
```
$ yum install numactl
```
  
第三次尝试 `rpm -ivh mysql-community-server-5.7.14-1.el6.x86_64.rpm`  
  
好啦，顺序是这样  
  
```
$ rpm -ivh mysql-community-common-5.7.14-1.el6.x86_64.rpm  
$ rpm -ivh mysql-community-libs-5.7.14-1.el6.x86_64.rpm  
$ rpm -ivh mysql-community-client-5.7.14-1.el6.x86_64.rpm  
$ rpm -ivh mysql-community-server-5.7.14-1.el6.x86_64.rpm  
```
  
启动服务  
  
```
service mysqld start
```
  
开机启动  
  
```
$ chkconfig --list | grep mysqld  
$ chkconfig mysqld on  
$ chkconfig --list | grep mysqld  
```
  
想登录了吗？ 呵呵，想太多了, 密码呢 ？？？在安装log里。。。 黑人脸.jpg  
  
```
$ cat /var/log/mysqld.log |grep password
```
  
有一行有 `A temporary password` blabla的最后的就是自动生成的密码, 麻烦给个提示行不行。。。
  
更改密码  
  
```
$ mysqladmin -u root -p password  
输入自动生成的密码  
输入新密码  
确认新密码  
```
  
呵呵，格式不符，格式不符 `Your password does not satisfy the current policy requirements`  
默认要求是8个字符，数字，字母，特殊符号  
受不了这个要求的话，你先用自动生成的密码，成功mysql -u -p 进入mysql后  
  
```
set global validate_password_policy=0;
set global validate_password_length=4;
```
  
第一句意思是把密码难度改为0, 即只检查长度  
第二句意思是把最低长度要求改为4位  
  
接下来开始你的为所欲为吧。。。 淫荡脸.jpg(不知道你会想起哪个jpg...)
  
  
  
  
  
嗯，别得意忘形了，utf8设置一下吧  
  
```
mysql $ show variables like '%character%';
```
  
只应该 `character_set_filesystem` 的值是 `binary`, 另外一个dir的是目录，其它的都应该是 `utf8`  
  
不是的话，就手动设置吧，简单。别去找my.cnf文件了  
  
```
set character_set_client = utf8;
```
  
里面有几个选项不是utf8的都可以通过这样set成utf8  
  
以上

