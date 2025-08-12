---
title: "创建GithubPages（未完成）"
date: 2025-08-12
---

## 0x00：关于

本文将要介绍一种使用`Github Pages`与`Jekyll`创建个人网站的方法

## 0x01：准备工作

需要准备的有：

Github账号

Git

魔法（可选）

## 0x02：创建Github仓库

在Github首页登录后，点击`New`进入仓库创建页面

在仓库名处填入`USERNAME.github.io`，并把`USERNAME`处的内容替换为你的Github用户名

这个仓库中不需要任何文件（之后我们会在本地创建），所以我推荐关闭`Add README`选项

点击`Create repository`创建仓库

记下仓库的SSH链接（形如`git@github.com:USERNAME/USERNAME.github.io.git`）

这个链接一般会显示在没有创建任何文件的仓库的主页面

## 0x03：配置Git与Github

点击右上角的你的Github头像，点击`Settings`，在左侧找到`SSH and GPG keys`并点击进入

先不管这个页面，在本地安装好Git后，进入`Git bash`运行如下指令

```shell
git config --global user.name "USERNAME"
```

```shell
git config --global user.email "EMAIL"
```

并把`USERNAME`与`EMAIL`替换为你的Github用户名与注册邮箱

之后运行

```shell
ssh-keygen -t rsa -C "EMAIL"
```

同样地，将`EMAIL`替换为你的Github注册邮箱

执行这一命令后，bash会输出`id_rsa.pub`文件的路径

使用

```shell
cat PATH_TO_PUBKEY
```

获取这一文件的内容并复制，注意要把`PATH_TO_PUBKEY`替换为刚刚提到的路径

回到上文提到的Github页面，点击`New SSH key`，在`Title`处填写任意内容，在`Key`处填写刚刚复制的内容

最后点击`Add SSH Key`即可

## 0x04：初始化你的主页


