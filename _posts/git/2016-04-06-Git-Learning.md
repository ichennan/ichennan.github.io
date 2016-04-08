---
layout: post
title: Git Learning
category: Git
tags: git github
keywords:
description:
---
## git & github  

这边会说说 `git` 和 `github` , 大概来说, `git` 就是工具, `github` 是大仓库  
你可以用 `github` , 也可以用什么 `abchub` 之类的, 或者只用本机, 总之 `github` 就是一个装东西的服务器  
但无论用 `github` , 还是 `abchub` , 还是只用本机(嗯，琼瑶姐姐就是这么赚稿费的), 用的工具都是 `git`  

你在 `github` 上有账号, 为自己的小项目建立了一个小仓库, 也就是创建了一个 `repository` , 假设名字叫 `firstProject`  
现在你要让 `github` 把你的电脑加为好友, 这样 `github` 就可以把项目发给你的电脑, 或者你在电脑上更改后发给 `github`  
怎么加为好友呢, 加 `qq` 好友是用 `qq` 号, `github` 就是用你电脑的 `ssh` 号  
`linux` , `Win` , `Mac` 下生成 `ssh` 的命令都差不多, 下面是 `linux` 的  

```
$ ssh-keygen -t rsa
```  

然后就会提示保存的位置之类的, 这条命令会生存两个文件 `id_rsa` , `id_rsa.pub`  
前面的是私钥, 后面是公钥, 你用记事本或者 `vim` 打开公钥, 复制里面的所有内容  
然后 `github` 上 `Edit Profile` - `Personal Settings` - `SSH and GPG keys` - `New SSH key` , 粘贴  

这样你就可以在本机上用 `git` 操作 `github` 了
你可以用下列命令去设置 `git` 的用户名, 邮箱之类的, 这样 `github` 上就会显示这个名字  
不然默认就是电脑的用户名, 所以跳过这步也可以  


```
$ git config --global user.name woshimingzi
$ git config --global user.email woshiyouxiang.com
```  

最后用这个命令验证一下  

```
$ ssh –T git@github.com
```

它会提示什么什么 `successfully` , `but` 什么什么, 就表示成功了  

## git  

然后就是从 `github` 上拖项目过来, 即使是空的  

```
$ git clone https://github.com/ichennan/firstProject
```  

这样就复制项目过来了, 之后你就在本地更改, 提交, 推送  
增加文件, 修改文件用 `add` , 删除文件用 `rm`  
`add .` `rm .` 表示所有  
提交 `commit` , 推送 `push`  
服务器送到本地 `pull`  
找不同用 `diff`  

```
$ git add abc.md
$ git rm def.md
$ git add .
$ git rm .
$ git commit
$ git push
$ git pull
$ git diff abc.md
```  

在 `commit` 这边要说一下, 通常文件有三种状态  

>Changes to be committed : 只有此状态下才会被push到github  
>
>Changes not staged for commit : 状态不对, 你需要add或rm, 或者checkout之后才能处理  
>
>Untracked files : 你需要add或rm先, 它们才能被commit  

通常来说 `git commit` 后面都需要加上 `-m abc` 表示注释, 如果不加, 会列出所有文件, 你需要删掉#号, 保存退出 `:wq` 后才会完成 `commit`  
ok, `git` 和 `github` 简单功能就这些了, 以后若有用到其它功能再新开一篇