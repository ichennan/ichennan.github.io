---
layout: post
title: Blc Version
category: Blc
tags: blc
keywords:
description:
---

```
<Resource name="jdbc/web" auth="Container" type="javax.sql.DataSource"
               maxActive="30" maxIdle="60" maxWait="10000"
               username="username" password="password" driverClassName="com.mysql.jdbc.Driver"
               connectionProperties="useUnicode=true;characterEncoding=utf8;"
               url="jdbc:mysql://localhost/broadleaf"/>
```  
  
```
url="jdbc:mysql://localhost:3306/broadleaf?useUnicode=true&characterEncoding=utf8"
```
  
```
<Connector port="8080" protocol="HTTP/1.1"
              connectionTimeout="20000"
              redirectPort="8443" 
              URIEncoding="UTF-8"/>
```