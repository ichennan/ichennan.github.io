---
layout: post
title: Blc Setup Properties
category: Blc
tags: blc
keywords:
description:
---

Spend one day here. What a fucking day !  
  
## Properties Sequence  
  
```
site  
../core/../runtime-properties/common-shared.properties  
../core/../runtime-properties/development-shared.properties  
../site/../runtime-properties/common.properties  
../site/../runtime-properties/development.properties  
  
admin  
../core/../runtime-properties/common-shared.properties  
../core/../runtime-properties/development-shared.properties  
../admin/../runtime-properties/common.properties  
../admin/../runtime-properties/development.properties  
  
VM options  
-Dproperty-shared-override=/Users/SomeUser/SomeProject/abc.properties  
-Dproperty-override=/Users/SomeUser/SomeProject/def.properties  
```
  
## hibernate.hbm2ddl.auto  
  
> **validate:** validate the schema, makes no changes to the database, show error if different  
  
> **update:** update the schema  
  
> **create:** create the schema, destroy previous data  
  
> **create-drop:** create, and drop the schema at the end of the session  
  
> **none**  
  
## My suggestion  
  
In `../core/../runtime-properties/development-shared.properties`  
Set it as below:  
  
```
blPU.hibernate.hbm2ddl.auto=update  
blCMSStorage.hibernate.hbm2ddl.auto=update  
blSecurePU.hibernate.hbm2ddl.auto=update  
```
  
when you first run or you want to clear all data  
*(complie `site.war` before `admin.war`)*  

```
../site/../runtime-properties/development.properties  
blPU.hibernate.hbm2ddl.auto=create  
  
../admin/../runtime-properties/development.properties  
blPU.hibernate.hbm2ddl.auto=none  
```
  
After first run, delete them  
  
```
../site/../runtime-properties/development.properties  
# blPU.hibernate.hbm2ddl.auto=create  
  
../admin/../runtime-properties/development.properties  
# blPU.hibernate.hbm2ddl.auto=none  
```


