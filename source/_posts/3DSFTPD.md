---
title: 3DS如何用FTP传输文件
date: 2020-03-19 16:26:42
catalog: true
tags: [游戏机,工具,3DS,分享]
categories: game
keywords: 3DS
---

<meta name="referrer" content="no-referrer"/>

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz9hgrjf2j30tc0tcwyp.jpg"/>

# 起因

放暑假的时忘记把读卡器带回家，这不要紧，因为有[FBI](http://nintendo-ds.dcemu.co.uk/-3ds-fbi-v2-5-3-1161570.html)——3DS上的无线安装软件，但是，FBI只是支持`cia`格式的安装包，且只能安装，不能进行文件的传输。

问题来了，一天，我突然想玩NDS的游戏，而有的NDS数字版游戏不支持在3DS上安装，一个实现的办法是在3DS游戏机上模拟NDS系统，实现套娃的操作——缺点就是耗电。

可是，因为模拟NDS系统不仅仅是安装一个软件那么简单，还需要到系统的根目录进行文件的拷贝修改等等。

那没有读卡器怎么操作？暂时又出不了门，又买不了。

原理很简单，在链接网络的情况下让3DS成为FTP（File Transfer Protocol，文件传输协议）**服务器即可**。

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz7o6iigxj33402c07wi.jpg"/>

# 操作环节

## FBI

大部分破解3DS游戏机都自带了这个软件，但是有的人手贱会删除它，比如我。这里我把它的链接放出来，之后使用SOON2安装即可。当然最近听到一些破解系统SOON2失效的消息。

<a href="https://pan.baidu.com/s/1i0nHw-n0SnwjliUYZo0elQ" class="LinkCard">FBI</a>

提取码：zozf

## FTPD

### FTPD介绍

FTPD软件为今天得重中之重，就是让3DS实现FTP服务器的软件啦，不过建议大一点的游戏就不要使用这个了，因为3DS本来不支持FTP还有其他各种各样的原因，反正速度是很慢（大概维持在1M/s左右），尤其是稍微大一点的游戏，传输过程之缓慢——亲身体验，毕竟我没读卡器。



### 在3DS端安装FTPD

在上面的百度云链接有FBI的电脑端，先安装，然后下载FTPD的cia文件，以及链接FTP的电脑端。

<a href="https://pan.baidu.com/s/1e_UUzBgP4ZgM2uRtR7-sLQ " class="LinkCard">FTP</a>

提取码：8tep

3DS连接WIFI之后，打开FBI

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz7wlfqh9j33402c04qq.jpg"/>

按`Y`键，你会看到一个`ip`地址

![IMG_2216.JPG](http://ww1.sinaimg.cn/large/006b3a9lgy1gcz87y4euuj33402c01ky.jpg)

打开电脑端的安装器，输入相应的ip地址，点击闪电标志测试是否能够连接。

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz8dkk695j30fl0bf0t8.jpg"/>

链接成功之后将`ftpd.cia`文件拖入，选中之后鼠标右键，发送即可。

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz8ia1ub8j30fl0bfwes.jpg"/>

安装完成之后会在3DS桌面看到一个礼物的图标，点开它，安装完成。

## 使用FTPD传输文件

### 3DS端

运行FTPD，同样可以看到一个`ip`，后面的5000是`端口`。

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz8ro4r57j33402c01l0.jpg"/>

### 电脑端

解压`flashfxp5_gr.zip`，运行`FlashFXP.exe`

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz8v1vsilj30ia0ast9r.jpg"/>

点击`会话`==>`快速连接`

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz8w1kjxsj31740pntb2.jpg"/>

输入相应的`ip`地址和`端口`，点击`连接`

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz8ysrjrhj30fu0a5t8y.jpg"/>

当右边出现3DS的文件目录说明成功。然后就可以操作了。3DS也会出现第一张图的画面。

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz91y7meqj31740pnq6j.jpg"/>

### 其他平台

像是其他平台如手机端都是可以进行操作的，道理相似，只需输入`ip`地址和`端口`即可。手机端可以下载如`ANDFTP`这类FTP链接的软件，甚至ES这种文件管理软件也是可以的。

# 后话

除非迫不得已，其实我是不建议使用此类方法的，一是因为麻烦，二是因为3DS读写能力以及其他方面的性能确实不给力——我们不能为难一台10年前的游戏机是吧？何况他还是老任家的呢？

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gcz9qa7mvej30tz0tz4cg.jpg"/>