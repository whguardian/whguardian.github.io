---
title: Java Thread about Thread and Runnable
date: 2016-09-01 11:14:36
tags: Thread
categories: Thread
---

### 错误命题：Runnable可以实现共享，Thread不能

<!--more-->

这是我们需要在了解Thread与Runnable之前需要了解的一个问题。之所以会有这样一个错误，主要是因为下面的这一种写法：

	Class RunnableThread implements Runnable() {...}
	...
	RunnableThread rThread = new RunnableThread();
	Thread threadOne = new Thread(rThread, "threadOne");
	Thread threadTwo = new Thread(rThread, "threadTwo");
	Thread threadThree = new Thread(rThread, "threadThree");
	threadOne.start();
	...

我只想说，朋友，侬脑子瓦特了吧！！！这是用Runnable在实现共享？？？这你是把Runnable共享给不同的Thread使用吧。当然，我也不知道运行上述代码到底会发生什么，因为我觉得连最基本的测试也不需要，原因在于如果你看过Google提供的Android doc就会知道导致上述这个错误命题的代码是多么的不切实际：

{% asset_img ThreadImp.PNG %}

很显然，在Thread的文档的最开始已经表明了Thread实现了Runnable接口......


