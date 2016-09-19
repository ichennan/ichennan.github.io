---
layout: post
title: Git Learning - 2
category: Git
tags: git github
keywords:
description:
---
## 不断补充Git知识中  

**ignore**  

根目录下添加 `.gitignore`  
*如果在添加 `ignore` 之前已经在仓库的文件, 需要 `git rm` 之后, `ignore` 才会起作用*  

```
.idea/
.vscode/
*.class
Thumbs.db
```  

**stash**  

本地和仓库有冲突时(也就是 `pull` 失败时), 覆盖本地版本  

```
$ git stash
$ git pull
```

**还原成github版本**  

git reset --hard HEAD