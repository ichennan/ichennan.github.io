---
layout: post
title: Blc Version
category: Blc
tags: blc
keywords:
description:
---
## Today is 2016-09-16  
  
### BroadleafCommerce in github:  
  
```
--admin  
  |--broadleaf-admin-functional-tests  
  |--broadleaf-admin-module  
  |--broadleaf-contenmanagement-module  
  |--broadleaf-open-admin-platform  
--core  
  |--broadleaf-framework  
  |--broadleaf-framework-web  
  |--broadleaf-profile  
  |--broadleaf-profile-web  
--common[broadleaf-common]
```
  
```
<groupId>org.broadleafcommerce</groupId>  
<artifactId>broadleaf</artifactId>  
<name>BroadleafCommerce</name>  
<version>4.0.11-SNAPSHOT</version>  
```

### DemoSite in github:  
  
```
--admin  
--core  
--site  
```
  
```
<groupId>com.mycompany-community</groupId>  
<artifactId>ecommerce-website</artifactId>  
<version>5.0</version>  
<name>ecommerce</name>  
```
  
```
<blc.version>5.0.3-GA</blc.version>  
<blc.menu.version>2.0.1-GA</blc.menu.version>  
<broadleaf-sample-payment-gateway.version>2.0.0-GA</broadleaf-sample-payment-gateway.version>
```
  

### DemoSite from blc.com:  
  
```
--admin  
--core  
--site  
```
  
```
<groupId>com.mycompany-community</groupId>  
<artifactId>ecommerce-website</artifactId>  
<version>5.0</version>  
<name>ecommerce</name>  
```
  
```
<blc.version>5.0.1-GA</blc.version>  
<blc.menu.version>2.0.0-GA</blc.menu.version>  
<broadleaf-sample-payment-gateway.version>2.0.0-GA</broadleaf-sample-payment-gateway.version>  
```


## My Solution  
  
### framework  
  
```
BroadleafCommerce  
branch: BroadleafCommerce-4.0.x  
> version: 4.0.11-SNAPSHOT -> 8.0.0-CN  
> Latest commit f0e641b  on May 18  
> @jefffischer jefffischer  
> Merge remote-tracking branch 'upstream/BroadleafCommerce-4.0.x'  
download zip  
```
  
### menu  
  
```
Menu  
branch: master  
> version: 1.0.0-GA -> 7.0.0-CN  
> Latest commit 672123d  on Jun 11, 2015  
> @phillipuniverse phillipuniverse  
> Merge tag 'broadleaf-menu-1.0.0-GA'  
download zip  
broadleaf-module-parent: 1.0.2-GA  
blc.version: 4.0.0-GA -> 8.0.0-CN  
```
  
### web  
  
```
DemoSite  
branch: master  
> version: 1.0 -> 9.0.0-CN  
> Latest commit e9d0673  on Dec 7, 2015  
> @phillipuniverse phillipuniverse  
> Merge tag 'broadleaf-4.0.5-GA'  
download zip  
blc.version: 4.0.5-GA -> 8.0.0-CN  
blc.menu.version: 1.0.0-GA -> 7.0.0-CN  
```