---
title: MySQL zip版配置
date:  2016-7-18 14:13:01
tags: MySQL
categories: MySQL 
---

>在MySQL上我们可以下载到MySQL zip版，我们只需要在下载完成后进行简单的解压而无需安装。但是zip版的MsSQL需要我们手动去配置，接下来就是简答的MsSQL配置过程。

<!--more-->

********************

#### 下载与解压MySQL

官方下载（Freeware版本）：[http://dev.mysql.com/downloads/mysql/](http://dev.mysql.com/downloads/mysql/)

根据需要下载需要的版本，下载完成后解压，建议解压到**全英语路径**。

#### 环境变量

从事Java开发的家伙一定知道怎么配置变量，与Java的环境变量配置相同，这个就不需要再研究了。接下来写给那些还没有配置过环境变量的同学：
**此电脑（我的电脑）--> 属性 -->高级系统设置 --> 高级 -->环境变量**

在**系统变量**中找到**Path**编辑，新建MySQL环境变量：

	;MsSQL-Path\your-MsSQL-folder\bin
	例：;E:\mysql 5.7.13\bin

**不要覆盖先前的环境变量，“ ; ”用于分隔各个环境变量。**

************************

#### my-default.ini配置

修改my-default.ini下的 **basedir = .......** 与 **datadir = ......** ：
basedir = （mysql路径）

	basedir = E:\mysql 5.7.13

datadir = （mysql下data路径）

	datadir = E:\mysql 5.7.13\data
	(zip版的mysql并没有包含data文件夹，需要我们稍后自己创建)

设置完成路径后**注意去除basedir 与 datadir前的“ # ”**。

#### 命令行

请以管理员身份打开cmd。
进入mysql\bin文件夹（其实配置完成环境变量后就没有进入bin的必要）：
> ~~(这玩意真不需要我写了)
D:\User\whguardian>e:
E:\>cd mysql 5.7.13\bin
E:\mysql 5.7.13\bin>~~

mysql服务安装：

	mysqld -install  

 > 服务移除：mysqld -remove

创建data文件（初始化）：
 
	mysqld --initialize
	
	说明：zip版的MySQL下并没有data文件夹，需要通过--initialize进行初始化。

> 亲爱的童鞋，如果！如果你按我上面的方法初始化了data文件夹。很好！！！那么我很不幸地告诉你，系统**很愉快**，**很友好**地为您的 **root** 用户添加了一个**密码**，一个非常简单的**密码**。
> 比如系统为我生成的密码：,G\<OTo-JG6hr
> (╯°Д°)╯︵ ┻━┻ ， ┻━┻︵╰(‵□′)╯︵┻━┻ ，┬─┬ ノ( ' - 'ノ) , (╯°Д°)╯︵ ┻━┻ 
> 还有一个问题，它并不会提示你密码的生成或位置.......
> 所以，接下来我们就要去寻找这个连自己也解不了的密码......
> 可获取密码信息位置：data\Yourhostname.err
> 在这个错误日志下可以找到这样一条记录：
> 2016-07-18T05:23:13.256676Z 1 [Note] A temporary password is generated for root@localhost: ,G\<OTo-JG6hr
> 后面跟随的就是自动生成的密码。

如果你不想系统很友好地为你生成一个密码，请在指令后加上 -insecure

	mysqld --initialize -insecure

开启服务：

	net start mysql

关闭服务：

	net stop mysql

