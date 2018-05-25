---
title: git ssh多邮箱配置
date: 2018-5-25 10:03:45
categories:
- git
tags:
- git
---

### 问题重现

我已经有了一个邮箱的ssh，这时候我用另一个公司邮箱注册了gitlab，而有个项目需要通过ssh访问公司服务器下载

<!-- more -->

### 再次生成ssh

1. 创建新秘钥

  `ssh-keygen -t rsa -C "youremail@yourcompany.com"`

2. 取名的时候另存为id_rsa_gitlab

  `Enter file in which to save the key (/c/Users/yourname/.ssh/id_rsa):/c/Users/yourname/.ssh/id_rsa_gitlab`

3. 之后一路回车

### 在.ssh目录下创建并配置config文件

```
Host github.com
    HostName        github.com
    User            git
    IdentityFile    /c/Users/yourname/.ssh/id_rsa

Host yourcompany.com
    HostName        yourcompany.com
    User            git
    IdentityFile    /c/Users/yourname/.ssh/id_rsa_gitlab

```

### 将id_rsa_gitlab.pub上传到公司服务器上，大功告成
