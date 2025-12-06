---
title: "如何创建并简单配置GithubPages"
date: 2025-08-12
categories: [Github, Life]
---

## 0x00：关于

本文将要介绍一种使用*Github Pages*与*Jekyll*创建个人网站的方法

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

先不管这个页面，在本地安装好Git后，进入*Git bash*运行如下指令

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

执行这一命令后，bash会输出*id_rsa.pub*文件的路径

使用

```shell
cat PATH_TO_PUBKEY
```

获取这一文件的内容并复制，注意要把`PATH_TO_PUBKEY`替换为刚刚提到的路径

回到上文提到的Github页面，点击`New SSH key`，在`Title`处填写任意内容，在`Key`处填写刚刚复制的内容

最后点击`Add SSH Key`即可

## 0x04：初始化你的主页

新建一个任意名字的文件夹，这个文件夹将要作为你的个人页面的根目录

在*Git bash*中进入该目录，使用`git init`命令初始化仓库

用`git checkout -b main`创建并切换到*main*分支

使用`git remote add origin REPO_SSH`链接远程仓库并将*origin*作为远端仓库的别名，其中`REPO_SSH`是之前记下的仓库的SSH链接

用`git fetch origin`和`git merge origin/main`与远程仓库进行同步（实际上这一步并不必要，这是以防万一）

创建`README.md`文件并编辑（MARKDOWN文件的编写在此处略），这是你的个人页面的主页面会显示的内容之一

创建`_config.yml`，这是Jekyll的配置文件

举例而言，你可以使用`theme:`指定主题，使用`title:`指定标题，使用`author:`指定作者，使用`description:`指定站点描述

在根目录下创建`_posts`文件夹，进入并创建命名格式为`YYYY-MM-DD-TITLE.md`的文件，其中`YYYY-MM-DD`为你文章的写作时间，`TITLE`为你文章的标题（最好是英文、数字、非特殊符号的组合），这个文件用来存储你的文章

在这个文件的开头加入如下的内容

```
---
title: "TITLE"
date: YYYY-MM-DD
---
```

这被称作“frontmatter”

同样地，`YYYY-MM-DD`为文章的写作时间，`TITLE`为文章的标题，需要注意的是，这里的两项不必须与上文的一致

回到根目录，用`git add .`将文件夹下所有内容加入提交缓存，用`git commit -m "DESCRIPTION"`提交更改，这里的`DESCRIPTION`是你关于这次更改的描述

最后，使用`git push origin main`将*main*分支推送到*origin*中的同名分支

## 0x05开启Pages

在你创建的Github仓库页面中找到并进入`Settings`，在左侧寻找`Pages`并点击进入

确保右侧的`Build and deployment`一栏下的`Source`被设定为`Deploy from a branch`，同一栏下的`Branch`被设定为`main`与`/(root)`

静静等待一些时间（时长不确定），进入`USERNAME.github.io`（这里的USERNAME是你的Github用户名）就可以看见你的页面

## 0x06其他

对于每篇文章的文件开头的部分（frontmatter），参见*[Jekyll frontmatter 文档](https://jekyllrb.com/docs/front-matter/)*

MARKDOWN的编辑教程参见*[MARKDOWN语法](https://markdown.com.cn/)*

有关主题的内容，参见*[主题模板 Themes | Jekyll 教程](https://jekylldo.cn/docs/themes/)*
