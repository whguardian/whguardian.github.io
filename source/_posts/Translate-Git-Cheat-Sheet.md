---
title: 简翻 Github - GIT CHEAT SHEET
date: 2016-07-17 23:40:01
tags:
  - Github
  - Git
categories:
  - Github
  - Git
---

工欲善其事,必先利其器 == 偷个小懒，不想记东西。Github作为超优秀的开源代码库，通过Git将代码，各类项目托管到Github，并且通过Git的版本管理实现项目，代码的优化等等。
如何使用Git，Github - GIT CHEAT SHEET中记录了基本的操作，本文将对其进行翻译（一个simple的笔记）。

<!--more-->

******************

### Github 
### GIT CHEAT SHEET


	Git是一款免费、开源的分布式版本控制系统，Github通过Git管理位于你笔记本，电脑中的项目与代码。这份小抄总结了常用的一些Git指令。

******************


#### Git安装

Github的桌面客户端提供了一个图形化用户界面，包含了大部分的项目库指令和为Git命令行提供的脚本

##### Github for Windows

[https://windows.github.com ](https://windows.github.com )

##### Github for Mac

[https://mac.github.com](https://mac.github.com)

###### Git for ALL Platforms
[http://git-scm.com](http://git-scm.com)

*****************

### 配置工具

为所有本地项目库设置用户信息

	$ git config --global user.name "[name]"

配置个人的用户名

*****************

	$ git congfig --global user,name "[email address]"

配置个人的邮箱

******************

	$ git config --color.ui auto

开启颜色提示帮助

*******************

### 创建项目库

新建一个项目库或从远程库克隆项目

	$ git init [project-name]

创建一个新的本地项目库

********************

	$ git clone [url]

使用 git clone 从现有 Git 仓库中拷贝项目

### 查看修改

### 分支管理

### 重命名

### 查看提交历史