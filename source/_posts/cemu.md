---
title: 如何在电脑用cemu玩塞尔达？
date: 2020-03-15 16:26:42
catalog: true
tags: [游戏,cemu,塞尔达]
categories: games
keywords: 塞尔达
---

<meta name="referrer" content="no-referrer"/>

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97e0roj31z4140qhg.jpg)

##  介绍//violetwsh.com

自从我卖掉PS4之后我就发誓不再买游戏机——作为学生党我是真的养不起。但是很多独占游戏让我十分羡慕，比如，买塞尔达送switch主机的塞尔达。后来在一次偶然的机会知道了cemu这个willu模拟器，并且之前也听说过，塞尔达最初不是在switch上发售的，但是因为willu上实在卖的太惨，后来才移植到switch上。

在新冠肺炎爆发之后，我被迫呆在家里，一天脑子抽风了然后入手一个Xbox s的手柄。

后来我想，Xbox手柄+cemu模拟器+塞尔达=等于正常玩塞尔达。于是去百度贴吧看了一下之后，果真还有，从此打开了新世界的大门，后来也玩到了女神异闻录5（PS3模拟器上）。

在开学前我也通关了120神庙+dlc。

在那几天的日子里，早上9点到早上3点，除了吃喝拉撒，就是塞尔达。

那么就让我们成为海拉鲁大陆的新流氓吧。

## 前期准备

1.一台性能过的去的电脑。尽管switch的性能问题总是被人拿来说事，但是由于系统不一样的原因，转换起来还是十分消耗性能的。

2.一个手柄。Xbox手柄，PS4手柄，国产手柄都可。个人建议国产手柄，像是北通这些都可。注意，玩塞尔达一定要有一个手柄，虽然键盘也能操作，但是毫无游戏体验。

3.cemu模拟器，点击[官网](http://cemu.info/)，可以前去下载安装。

4.cemu hook，支持cemu的CG播放插件。点击[官网](https://cemuhook.sshnuke.net/)，下载与模拟器对应版本即可，下载之后解压即可。

5.塞尔达游戏本体。[老男人游戏网]([https://www.oldmanemu.net/%E5%AE%B6%E6%9C%BA%E6%B8%B8%E6%88%8F/wiiu/wiiu%E4%B8%AD%E6%96%87%E6%B8%B8%E6%88%8F%E5%85%A8%E9%9B%86](https://www.oldmanemu.net/家机游戏/wiiu/wiiu中文游戏全集))，游侠都可找到，注意是willu版本的就是了。如果实在找不到可以留言。

6.WUP转loadiine工具。这个是将游戏文件转换为模拟器可读的工具。[点击提取](https://pan.baidu.com/s/1l59-MGikVJikSO40E_weGQ)，提取码：fw12 

当然，如果你嫌弃麻烦的话，可以用我的，可以省去3，4，5步骤，但是cemu版本比较低，但是亲测可用。（毕竟我都通关了）[点击提取](https://pan.baidu.com/s/1WJMr5BbrmFgqdeMnZ1P5yw)，提取码：e2rt。



## 初期设置

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97fw4zj31000lnwer.jpg)

首先打开是这个界面，我们点击菜单栏的`Options`>>>`General settings`，可以看到`Language`选项，将它改为Chinese，直接`×`掉，点`ok`，退出重启之后就会发现界面是中文了。

依次点击菜单栏的`CPU`>>>`模式`，然后选择最大核编译。

依次点击菜单栏的`选项`>>>`GPU缓存精度`，根据自己的情况选择质量，这里我选择的事高质量。

（使用我提供的文件的可以跳过此步骤）依次点击菜单栏的`选项`>>>`常规设定`，点击`图像`，在常规栏下的Graphics API选择OpenGL。

其他根据自己的情况选择。

### 手柄设置

依次点击菜单栏的`选项`>>>`输入设定`。我们会看到一下画面：

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97un8sj30sg0g4jrl.jpg)

1.配置文件先输入一个名字。

2.模拟器控制选择Will U Gamepad或者Will U  Pro Controller。

3.控制器API一栏，Xbox手柄选择Xinput，其他手柄选择Directinput。

4.控制器一栏下拉选择自己的控制器。

5.在对应的按键后的方框按下手柄对应的按键。

以Xbox手柄为例，LB对应L，RB对应R，LT对应ZL，RT对于ZR。“+” “-”键我用的是手柄面板中间两个按键。摇杆的click对应的是手柄摇杆按下。震动建议拉到100%。

完成后如图：

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97j3voj30sg0g40te.jpg)

先点击`保存`，再在配置文件选择配置好的文件点击`载入`。

手柄的设置就算是大功告成了。

### 文件的转换

（使用我提供的文件的可以跳过此步骤）

像是塞尔达这种比较出名的游戏大多下载之后的是不需要转换的，别人是提前转换好了的。下载WUP转loadiine工具解压之后是这个样子的。顾名思义，就是将游戏tik文件拖到![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97jsaoj303w00lgld.jpg)

转换器就会在游戏目录生成一个`code`文件，就表示成功了。

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97jsigj30hy0260sm.jpg)

### 性能优化

cemu模拟器在电脑上很多情况下没有得到一个很好的性能。我们需要自己手动设置。

1.在桌面右键，点击NVIDIA控制面板。

2.依次点击 `3D设置`>>>`管理3D设置`>>>`程序设置`，界面如图所示

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97tfimj30r20icgnu.jpg)



我们点击`添加(D)`



![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97rgo6j30dt0hrwf8.jpg)



点击`浏览(B)`，之后找到自己cemu安装目录下的`Cemu.exe`，选中之后点击打开即可。

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97t2k4j30qo0f0gmu.jpg)



回到NVIDIA控制面板，在`2.制定该程序的设置值(C)`栏设置相应的参数，我的设置如下：



![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97utr7j30qv0t3mzg.jpg)

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx97yy90j30fg08et98.jpg)

其实这里最重要的是`OpenGL 渲染GPU`以及`电源管理模式`，其他参数都是可有可无。

#### PS

如果后期玩游戏时发现画面有撕裂感的话可以回到这里将`垂直同步`打开。

## 游戏的载入

准备工作做完之后就可以载入游戏了，在手柄连接的情况下打开cemu，点击菜单栏的`文件`>>>`载入`。

还记得之前转换游戏文件时有一个`code`文件夹吗，选中`code`文件夹下的`U-King.rpx`文件，点击`开启`，就可以载入了。第一次载入时间较长，之后会快一些。

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx982yuej30qo0f0gmc.jpg)

效果如图

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx99077wj31000ln4qp.jpg)

然后点击菜单栏的`设定`>>>`全屏`就可以开始全屏游戏。

从此，你也是海拉鲁大陆的一名老流氓了。

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx98peudj31000lnkjl.jpg)

//violetwsh.com

## 进阶设定

### 图形包

cemu提供了一些图形包，在菜单栏下的`设定`>>>`图形包`（1.17版本是`图像插件`）里。

勾选相应的图形包即可，在Cemu 1.13.1版本下我勾选的是（仅供参考）：

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx98p1izj30e80grjsk.jpg)

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx98t49jj30e7054jrk.jpg)

cemu1.17的图形界面找到塞尔达旷野之息（The Legend of Zelda: Breath of Wild）

在1.17版本下，具体的图形包设置可以参考这个[帖子](https://tieba.baidu.com/p/6172035119?red_tag=1341829710)

### NFC(amiibo)的设定

任天堂的一些手办带有NFC功能，在游戏中使用amiibo每天可以刷一些东西。

[塞尔达NFC文件下载](https://pan.baidu.com/s/1hPlljU22AmY-27kUTE8OEA) 提取码：ukds

1.在进入游戏时选择`选项`，在第一栏的amiibo设定中打开即可。

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx9aaplmj31000ln7is.jpg)

2.在游戏切换道具，使用道具。



![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx9c77ywj31000lw1fi.jpg)

3.进入游戏，点击菜单栏的`NFC`>>>`从文件载入NFC标签（Amiibo）`,选择一个`.bin`后缀文件。

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx9cbcv6j31000lwe81.jpg)

## 最后

神庙都没有通关救什么塞尔达公主（狗头），还有，米法天下第一！！！

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx9dkm8mj31hc0u01ky.jpg)

![img](http://ww1.sinaimg.cn/large/006b3a9lgy1gcwx9e3ed1j31hc0u0u0z.jpg)

//violetwsh.com
