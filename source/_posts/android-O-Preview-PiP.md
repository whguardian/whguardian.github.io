---
title: android O Preview PiP
date: 2017-05-21 21:47:16
tags:
---
PiP，即Picture-in-Picture Mode并不是一个全新Android的特性，在Android TV中我们已经见到过这个特性。现在，在Google I/O 2017上Google正式将这个特性引入到Android Mobile中，我们可以使Activity运行在PiP mode上。

<!--more-->

PiP是一种多窗口模式，经常被使用于视频的播放。请注意，Android的PiP mode并不是一种全新的设计，我们已经看到一些应用能够一悬浮窗的形式播放视频，如MoboPlayer，这是一款国产的App能够在点击home键后将App显示为一个悬浮窗口。

---------------------------------------------------------------

### 环境

---------------------------------------------------------------


* Android SDK 25
* Android Build Tools v25.0.3
* Android Support Repository

### 未定标题

---------------------------------------------------------------

#### 在PiP下Activity的状态改变

当一个应用进入PiP mode后，应用将被*pause*，之所以这样的原因是因为 **Multi-Window Lifecycle** 。
因此，我们可以首先回顾一下有关与 **Multi-Window Lifecycle** 的内容(不知道也没有关系，简单理解一下就okay了)。 **Multi-Window Lifecycle** 是在 Android N 中被引入的显示特性，可以使两个应用同时被显示(当一个在前台屏幕上运行时，长按menu键可以进入**split-screen mode**，或在**Overview screen** 中长按menu，然后将一个应用拖入**split-screen mode** )。
**Multi-window mode does not change the activity lifecycle**，这是Google在android的开发文档中明确指出的一点。只有最近与用户有交互的应用才是处于 **active** 状态，所有其他的应用都将进入 **paused** 状态。通过与 **paused** 状态下的应用的交互将交换应用的状态(交换这个词在这里使用的不是很合理，因为应用状态的切换是由系统调用，并且是单独改变应用的状态，而不是真正意义上地交换状态)。一下是Google 的一些note:

> **Note**: In multi-window mode, an app can be in the paused state and still be visible to the user. An app might need to continue its activities even while paused. For example, a video-playing app that is in paused mode but is visible should continue showing its video. For this reason, we recommend that activities that play video not pause the video in their onPause() handlers. Instead, they should pause video in onStop(), and resume playback in onStart().









### Google Sample

---------------------------------------------------------------

Get it on GitHub: [Java](http://github.com/googlesamples/android-AutofillFramework/)|[kotlin](http://github.com/googlesamples/android-PictureInPicture/tree/master/kotlinApp)

### 资料链接

---------------------------------------------------------------

[Multi-Window Support](https://developer.android.com/guide/topics/ui/multi-window.html#lifecycle)

