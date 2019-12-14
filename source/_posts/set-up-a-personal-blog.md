---
title: 个人博客搭建记录 —— Github + Hexo
date: 2016-07-16 14:10:00
categories:
 - Blog
 - 博客
 - Github
tags: 
 - Disqus
 - Git
 - Github 
 - Hexo
 - NexT
---
一个自建的博客向来是一件很酷的事情，但也往往是一件很(╯°Д°)╯︵ ┻━┻ 的事情，所以，选择一个简单的方法可以.......，→_→。Github + Hexo是就是这么一个简单粗暴的组合。接下来我建立博客的过程记录下来。
以下是需要使用的环境，框架等等......

<!--more-->

搭建工具:   

Tools  |          URL                           | Detail
-------|----------------------------------------|----------
Hexo   |[hexo.io](https://hexo.io)              | 静态博客框架
Git    |[git-scm.com](http://git-scm.com)       | 分布式版本控制系统
Node.js|[nodejs.org/en](https://nodejs.org/en/) | JS运行环境                                    
NexT   |[theme-next.iissnan.com](http://theme-next.iissnan.com/)                              | 博客主题
Disqus |[disqus.com](https://disqus.com/)       | 社会化评论系统
Github |[github.com](https://github.com)        | 博客搭建位置


**Ps: 本文仅针对Windows用户，Mac OS， Linux用户 谢谢惠顾**
************************

### Github + Hexo创建博客
整个个人博客是建立与Github + Hexo。
Github为我们提供了一个免费空间以帮助我们创建博客，Hexo可以在本地生成博客，并将它发布到Github上。
#### Github
我们需要搭建的个人博客依赖于Github，这是一个免费的开源代码库以及版本控制系统（什么！！！你不知道Github，那你现在看到的博客是在什么地方，出门左转去看看Github）。
##### 注册Github
想要在Github上创建一个个人博客，需要**申请一个Github的账号**。申请过程如下：... ... ... ...（博主实在太懒，其实只是需要一个邮箱注册）。
##### 在Github上创建仓库
接下来，我们要为博客**申请空间（即，在Github上创建一个仓库）**。这个仓库与一般我们存放项目的仓库没有区别，只不过需要一个特定的命名，创建过程如下：
**Repository name有固定格式：username.gituhub.io，username既是你的Github用户名，github.io固定不变**

#### Hexo
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

* 超快速度
* 支持 Markdown
* 一键部署
* 丰富的插件  

安装Hexo的过程十分简单，但在安装时电脑上必须已经安装如下应用程序：

* Git
* Node.js

##### Git
通过Git我们可以将本地的Hexo发布到Github上
Git下载地址：[git-scm.com/downloads](https://git-scm.com/downloads)
**（如果电脑上已经安装呢了Github for Windows就无需再安装Git）**
###### 创建用于发布到Github的SSH key
如果我们要将本地的项目通过Git发布到Github上我们需要生成一个SSH key并在Github上登记（安装Github for Windows时同时会在用户目录下创建一个**.ssh**文件夹，无需再创建SSH key）
	
	使用Git生成SSH key：
	打开Git Bash
	$ cd ~/.ssh   
检测是否存在.ssh文件夹，如不存在将提示：No such file or directory创建SSH key
	
	$ ssh-keygen -t rsa -C "User@youremail.com"   
**注意格式：ssh-keygen，-C为大写
在上述指令后回车三次，分别出现下面三行指令:

	Enter file in which to save the key (/d/Users/whguardian/.ssh/id_rsa): 
	Enter passphrase (empty for no passphrase):
	Enter same passphrase again:
依次为生成的SSH key的 文件名（无需记录，随意），密码，确认密码，三个都可以不填

在Github上记录SSH key：
验证记录正确，打开Git Shell输入（一字不改）：

	ssh -T git@github.com

##### Node.js
Hexo依赖于Node.js生成静态网站
Node.js下载地址：上方Node.js官网主页
##### 安装Hexo
	$ npm install -g hexo-cli
##### 建站
主要命令：

	$ hexo init <folder>
	$ cd <folder>
	$ npm install
通过hexo init在指定位置创建博客文件夹：
使用Git Shell到指定盘符或文件夹下创建文件夹（以E: 为例创建一个Blog文件夹）：

	F:\> e:
	E:\> hexo init Blog
**也可以直接在指定盘符或文件夹直接右键Git Bash后hexo init Blog**
进入创建的文件夹：**cd Blog** （如果文件夹有多个单词将命名一引号框起来）
安装Hexo在文件夹下： **npm install**
新建完成文件夹下目录：

	.
	|── _config.yml
	|── package.json
	|── scaffolds
	|── source 
	|       |── _drafts
	|       |── _posts
	|── themes
##### **第一次部署（本地部署，未上传到Github）**
	$ hexo generate
	$ hexo server

##### 预览
在浏览器中输入：**localhost:4000** 预览，在shell中按**Ctrl + C**停止server
##### 发布到Github
修改Blog文件下的**_config.yml**，这是hexo博客的配置文件。修改deploy标签下信息（deploy在文件末尾）

	deploy: 
	  type: git
	  repo: https://github.com/whguardian/whguardian.github.io.git,master
**type: repo: 后跟一个space，格式不能有任何更改**
发布到Github

	hexo deploy

每次发布到Github时，都需要执行

	hexo generate
	hexo deploy

**偷工减料：generate可以写为g，deploy可以写为d，并且两个可以互相为参数，如下：**

	hexo generate -d
	hexo deploy -g

***********************************************
### 主题 与 评论，分享
#### NexT主题
Hexo有许多的主题主题以使用户能够定制自己的个性博客（其实是我不喜欢默认的主题，要不然谁愿意做麻烦事，┻━┻︵╰(‵□′)╯︵┻━┻ ）。这里我选择的是NexT，（随大流，随大流）。
##### 下载主题并启用
在使用主题前，我们需要将主题先克隆到我们的Hexo上。

	cd Blog
	git clone https://github.com/iissnan/hexo-theme-next themes/next

当然，也可以从相关网站下载主题：https://github.com/iissnan/hexo-theme-next/releases
**注意：**在clone完成后，我们在Blog文件下将有两个_config.yml。一个是Hexo的，一个是在Blog/themes/your theme下的_config.yml。NexT将前一个称之为**站点配置文件**，在theme下的为**主题配置文件**。
完成clone后，修改_config.yml下theme
	
	theme: next

不要问我大小写，我也没有试过，但是！！！theme: 后一定要跟一个space，一定要跟一个 space，一定要跟一个space。
##### 主题设定
NexT同时还为我们三个不同的外观，通过更改**主题配置文件**中的scheme的值来更改主题

	# Schemes
	#scheme: Muse
	scheme: Mist
	#scheme: Pisces

* Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
* Mist - Muse 的紧凑版本，整洁有序的单栏外观
* Pisces - 双栏 Scheme，小家碧玉似的清新

通过去除scheme前#来设定这个外观，如果没有scheme则自己手动输入，记住**不要漏scheme: 后的space**。

#### NexT主题配置

通过修改 **站点配置文件** 或 **主题配置文件** 来修改NexT。

##### 界面语言：站点配置文件

	language: zh-Hans    //简体中文

NexT支持的语言

语言|代码|设定示例
-----|----|-----
English  |	en |	language: en
简体中文   | 	zh-Hans |	language: zh-Hans
Français |	fr-FR	 | language: fr-FR
Português |	pt	 | language: pt
繁體中文 |	zh-hk 或者 zh-tw	| language: zh-hk
Русский язык |	ru	| language: ru
Deutsch  |	de	| language: de
日本語	|ja  |	language: ja
Indonesian | id	| language: id

##### 菜单：主题配置文件
#####  社交链接：主题配置文件
将自己的微博，Twitter分享给全世界的人。链接被防止在**主题配置文件**的social字段中，其键值格式是 显示文本: 链接地址。

	social:
	  Github: https://github.com/username
	  Twitter: https://twitter.com/username
	  Weibo: http://weibo.com/username

为上面的社交链接设置图标，社交图标来自[Font Awesome](http://fontawesome.io/)

	social_icons:
	  enable: true
	  # Icon Mappings.
	  # KeyMapsToSocalItemKey: NameOfTheIconFromFontAwesome
	  GitHub: github
	  Twitter: twitter
	  Weibo: weibo

#### Disqus评论系统
这是我最开心的部分，:D，Disqus评论系统。至于为什么开心，原因很简单，这玩意基本改一行就ok啦！！！Tell me，你有什么理由不选它......
当然，要用它基本的注册还是需要的。
##### Disque注册与短域名
##### Disqus配置
修改**主题配置文件**添加社会化评论系统到博客中：

	#Disqus
	disqusshortname: your shortname //不需要再强调space了吧

#### 分享

通过**社交分享插件**来实现分享功能。网上有许多分享插件，**AddThis**，***多说分享**，**JiaThis**，**百度分享**......我选择的是AddThis作为博客的第三方分享。AdThis是国外的第三方分享，之所以选择它是因为它将几乎所有的社交书签的网站集合在一起，我们几乎能分享到任何一个SNS。

AddThis：[http://www.addthis.com/](http://www.addthis.com/)

前提：修改**站点配置文件**下**url**节点，

	url: http://yoursite.github.io

##### AddThis

注册AddThis，注册一个分享按钮：

	1. Add Profile：添加一个新的Profile
	2. 点击Tools：选择Tools下一个选项 SET UP
	3. Activate：自定义设置分享按钮，完成后Activate
	4. Continue：直接点击CONTINUE（不需要复制JS，NexT中内置）
	5. 点击 ···：复制General的ID

##### 添加分享服务

**主题配置文件**，_config.yml下解除**add\_this\_id**注释，去除“ # ”，在后面添加AddThis ID。

***********************************************

### 博客文章创建与发布

#### 创建博客

	$ hexo new "your Blog name"

#### 博客编辑

博客创建完成后，将在 ?:\Blog\source\_posts中创建一个以“ your Blog name”命名的.md文件，通过编辑.md文件我们就可以完成博客的编辑。
如何打开.md文件，童鞋们可能想到了万能的**记事本**，但是，直接用记事本编辑的.md文件很容易出现乱码，所以，放弃这个念头吧。

	我使用的md编辑器：StackEdit
	StackEdit是一个在线的md编辑器，当然，它是免费（不然为什么选它呢！！！）

StackEdit编辑器网址:[https://stackedit.io/editor#](https://stackedit.io/editor#)
md文件由Markdown这种标记言语编写，关于Markdown的语法，下面有一个我自己写的示例链接：
[https://github.com/whguardian/README-MD](https://github.com/whguardian/README-MD)
如果想要深入了解Markdown大家可以自行Google，百度。

##### Front-matter 

在生成博客md文件时，博客中已经包含了一些内容，这些内容既是**Front-matter**，通过 “ **- - -** ”被分隔在文件头部。如下：

-----------

\-\-\-
title: 我创建博客的“传奇历程”
date: 2016-07-16 14:10:00
categories:
 \- Blog
 \- 博客
 \- Github
tags: 
 \- Hexo
 \- Git
 \- NexT
 \- Disqus
 \- Github 
\-\-\-

----------------

Front-matter中声明了如**文章标题**，**创建时间**，**类别**，**标签**，**评论功能**等描述博客的参数。关于这部分的内容可以查看hexo的官方文档：[https://hexo.io/zh-cn/docs/front-matter.html](https://hexo.io/zh-cn/docs/front-matter.html)。

#### 发布博客

见 **发布到Github**


***********************************************

### 域名绑定

除了使用Github为我们提供的二级域名，我们还可以绑定自己的域名到博客。

#### 域名解析

个人在 **GoDaddy** 与 **万网** 注册过域名，现在使用的是GoDaddy。注册GoDaddy和域名申请我就不介绍了。这里我们想要一个二级域名来指向博客，需要域名解析。

GoDaddy：[https://sg.godaddy.com](https://sg.godaddy.com)

域名解析：

	右上角 用户名 --> 管理域名 -->（切换到列表视图）--> 点击使用的域名 --> DNS区域文件

修改CName标签下内容，添加编辑 **主机：（用户自定义）**，**指向：yoursite.github.io**。修改完成后DNS服务器需要时间进行解析。

#### 博客识别域名

在Blog\source下创建**CNAME**（没有后缀名）文件，添加域名到CNAME。

	添加域名实例：blog.whguardian.info

部署到github。

注：**不建议在国内注册和只用CN域名，其他也不多说，只是你并不能获取CN的完全所有权，并且存在被 域名暂停解析 的风险，也就是说你将无法使用你的CN域名，CN域名将被禁止访问，WTF。** 

***********************************************

### 完成

以上就是有关于 **Github + Hexo 个人博客**的搭建，发布内容，也是对我创建自己的个人博客的一个总结。



