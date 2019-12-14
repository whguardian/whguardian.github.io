---
title: Android App Resources (draft)
date: 2016-09-03 00:01:43
tags:
 - Android
 - res
categories:
 - Android
 - XML
---

白天有朋友问我了一个关于Android res下Mipmap的问题，现在突然心血来潮想要看看有关于这一方面的东西。关于Android App Resources的问题并不想代码一样麻烦，我们可以直接去Android Developer上查看相关的描述。我也向通过这篇blog来巩固一下有关与res的知识。  
整篇基本概括了Android Develope对Resources一些简单解析。  

<!--more-->

### 概述

我们在开发时应该将需要的资源外部化，这些资源包括图像，字符串（例：将Button的text保存到res下而不是直接输入是一个好习惯），并且，通过将资源外部化还可以适配不同的设备。  
我们在引用资源时不许确保至少有一个被指定的资源，一般情况下每一个资源都将存在一个默认资源，并且通过**配置修饰符**设置**可选资源**。  

* 每一个资源都应该存在一个默认资源防止运行奔溃。
* 通过配置修饰符用于指定特定配置的资源 。
* 配置修饰符可以连用。

### 提供资源

将应用的资源外部化有利于对资源的维护

#### 资源文件分类

在创建Android Project时，Android Studio将自动在main\res下生成部分资源目录与路径

{% asset_img ResFolder.PNG %}

这是一个在创建拥有一个空白Activity时生成的res，包括**drawable**(图像)，**layout**(布局)，启动器图标的**mimap**，**values**(简单值)，values中又包括**colors，dimens，strings，styles**。

> 区分mipmap与drawable的不同，mipmap并不是为了替代drawable

**表1**.项目 res/ 目录内支持的资源目录

目录       | 资源类型
--------- | --------------
animator/ | 用于定义[属性动画](https://developer.android.com/guide/topics/graphics/prop-animation.html)的XML文件。
anim/     | 定义[渐变动画](https://developer.android.com/guide/topics/graphics/view-animation.html#tween-animation)的XML文件。
color/    |  
drawable/ | 
mipmap/   |
layout/   | 用于定义用户界面布局的XML文件。[布局资源](https://developer.android.com/guide/topics/resources/layout-resource.html)。
menu/     |
raw/      |
values/   |

##### 关于mipmap 

网上流传这一种神奇的说法，Google推荐使用mipmap替换drawable，但是事实上，Android Developer上只是推荐将启动器图标放置到mipmap中，除此之外mipmap暂时没有其他任何的作用。以下是在Android Developer中关于**管理启动器图标作为mipmap资源**的原文

原文地址: [Add Bitmap Images with Image Asset Studio](https://developer.android.com/studio/write/image-asset-studio.html)
> **Managing Launcher Icons as mipmap Resources**
> 
>  -------------------------------------------------------------
> Different home screen launcher apps on different devices show app 
launcher icons at various resolutions. When app resource optimization techniques remove resources for unused screen densities, launcher icons can wind up looking fuzzy because the launcher app has to upscale a lower-resolution icon for display. To avoid these display issues, apps should use the mipmap/ resource folders for launcher icons. The Android system preserves these resources regardless of density stripping, and ensures that launcher apps can pick icons with the best resolution for display.
Make sure launcher apps show a high-resolution icon for your app by moving all densities of your launcher icons to density-specific res/mipmap/ folders (for example res/mipmap-mdpi/ and res/mipmap-xxxhdpi/). The mipmap/ folders replace the drawable/ folders for launcher icons. For xxhpdi launcher icons, be sure to add the higher resolution xxxhdpi versions of the icons to enhance the visual experience of the icons on higher resolution devices.
>> **Note**: Even if you build a single APK for all devices, it is still best practice to move your launcher icons to the mipmap/ folders.

#### 配置修饰符

**表2**.配置修饰符

优先级 |          配置           |    修饰符值     | 描述
------|----------------------- | -------------- | ----
1     | Country Code           |    示例：mcc310            |             
2     | Network Code           |    示例：mnc004            |
3     | Locale                 |    示例：en fr zh-cn
4     | Layout Direction       |    ldrtl ldltr
5     | Smallest Screen Width  |   sw < N > dp<br/>示例：sw320dp
6     | Screen Width           |   w < N > dp
7     | Screen Height          |   h < N > dp
8     | Size                   |small<br/>normal<br/>Large X-Large
9     | Ratio                  | long<br/>notlong
10    | Orientation            | port<br/>land
11    | UI mode                | car<br/>desk<br/>television appliance watch
12    | Nigth Mode             | night<br/>notnight
13    | Density                | nodpi<br/>anydpi<br/>ldpi<br/>mdpi<br/>hdpi<br/>x-hdpi<br/>xx-hdpi<br/>xxx-hdpi
14    | Touch Mode             | notouch<br/>stylus<br/>finger
15    | Keyboard               | keysexposed<br/>keyshiden keyssoft
16    | Text Input             | nokeys<br/>qwerty<br/>12key
17    | Navigation State       | navexposed<br/>navhidden
18    | Navigation Method      |  nonav<br/>dpad<br/>trackball wheel
19    | Dimension              |  < M > x < N ><br/> 示例:320x426
20    | Version                | 示例：v21 |<a href="#apiLexel">附录</a>
 
#### 资源

#### 资源ID

### 访问资源

### 本地化

### 附录

#### <a id="apiLexel">API Level</a>

Platform Version | API Level | VERSION_CODE
------------------ | ------- | ----
Android 7.0        | 24      | NOUGAT
Android 6.0        | 23      |MARSHMALLOW
Android 5.1        | 22      | LOLOPOP_MR1
Android 5.0        | 21      | LOLIPOP
Android 4.4w       | 20      | KITKAT_WATCH
Android 4.4        | 19      | KITKAT
Android 4.3        | 18      | JELLY_BEAN_MR2
Android 4.2,4.2.2  | 17      | JELLY_BEAN_MR1
Android 4.1,4.1.1  | 16      | JELLY_BEAN 
Android 4.0.3,4.0.4| 15      | ICE_CREAM_SANDWICH_MR1
Android 4.0, 4.0.1, 4.0.2| 14| ICE_CREAM_SANDWICH
Android 3.2        | 13      | HONEYCOMB_MR2
Android 3.1.x      | 12      | HONEYCOMB_MR1
Android 3.0.x      | 11      | HONEYCOMB
Android 2.3.4<br/>Android 2.3.3|10 | GINGERBREAD_MR1
Android 2.3.2<br/>Android 2.3.1<br/>Android 2.3| 9     | GINGERBREAD
Android 2.2.x      | 8       | FROYO
Android 2.1.x      | 7       | ECLAIR_MR1
Android 2.0.1      | 6       | ECLAIR_0_1
Android 2.0        | 5       | ECLAIR
Android 1.6        | 4       | DONUT
Android 1.5        | 3       | CUPCAKE
Android 1.1        | 2       | BASE_1_1
Android 1.0        | 1       | BASE