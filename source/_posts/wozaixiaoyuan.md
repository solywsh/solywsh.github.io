---
title: 我在校园自动打卡脚本
date: 2021-01-10 18:26:00
catalog: true
tags: [python,脚本]
categories: python
---

<meta name="referrer" content="no-referrer"/>

## 我在校园自动打卡脚本(部署在服务器上)

很久没有跟新了，要不是腾讯云提醒我域名要到期我都快忘了我还有个博客，最近疫情的原因每天总是需要打卡，但是有些时候还得专门定闹钟起来给自己打卡，就很烦。

得知网安那边搞了个自动打卡的脚本最开始我是很兴奋的，毕竟可以偷懒了，但是我听说Token只能有效4天，于是我又放弃了打算。

在几天前韩松傲给我解释了为什么无法自动得到Token的原理之后，~~虽然我没听懂~~，但是我还是明白一个道理，反正我是没办法了，当然，要是有办法也轮不到我在这写这个教程了。

### 声明

{% note danger %} 

此脚本更改和公开已经得到某位秦姓男子的同意，我就当他们同意了。

此脚本只是用于分享，切勿用于不法通途。

此脚本并没有解决原来脚本的弊端，只是增加了提醒功能而已。

{% endnote %}

### 教程

#### 前期准备

- charles抓包工具获取token，可以去官网下载

<a href="https://www.charlesproxy.com/download/" class="LinkCard">charles</a>

 也可以试试直接点下面的链接，~~如果还没失效的话。~~

<a href="https://www.charlesproxy.com/assets/release/4.6.1/charles-proxy-4.6.1-win64.msi?k=993432c69c" class="LinkCard">charles下载</a>

- python运行环境
- 微信电脑版
- （可选）24小时运行的服务器，装上宝塔面板

#### charles相关

打开charles，由于有些人第一次用，有些地方可能不知道，我先说一下charles的前期配置。

- 安装证书，可以看下面的教程，下面的教程转自简书。

  <a href="https://www.jianshu.com/p/8346143aba53" class="LinkCard">charles证书安装</a>

![img](https://upload-images.jianshu.io/upload_images/12861759-886a4cf6ebbbde2f.png?imageMogr2/auto-orient/strip|imageView2/2/w/977/format/webp)



![img](https://upload-images.jianshu.io/upload_images/12861759-15eca07692c21f42.png?imageMogr2/auto-orient/strip|imageView2/2/w/446/format/webp)



![img](https://upload-images.jianshu.io/upload_images/12861759-49350fae1201d4f7.png?imageMogr2/auto-orient/strip|imageView2/2/w/555/format/webp)



![img](https://upload-images.jianshu.io/upload_images/12861759-55c8ca710a3d7d1c.png?imageMogr2/auto-orient/strip|imageView2/2/w/555/format/webp)



![img](https://upload-images.jianshu.io/upload_images/12861759-5276527aabe9dbd0.png?imageMogr2/auto-orient/strip|imageView2/2/w/612/format/webp)



好了，到这里证书安装完成。

- **安装证书好之后，去 `Proxy-> ssl  proxying settings`，添加一个443端口**，这里很重要。

![img](https://img-blog.csdn.net/20180615135359223?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JpbmdodWl6aTE5OTI5Mw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



- 然后打开本地代理`proxy->windows iproxy`



#### 得到token

charles不要关，登陆电脑微信，打开我在校园。

这时，charles会出现一个链接为`https://student.wozaixiaoyuan.com `的地址，这就是我在校园的地址。

找到改目录下`student`->`home.json`->`Content`->`token`(其实也不一定，只要找到Content里是有Token的目录就行)

![QQ截图20210110211304.png](http://ww1.sinaimg.cn/large/006b3a9lly1gmiwrphq24j30qv0t3taq.jpg)

这时我们就得到token了。

#### 下载脚本

去我的仓库下载[Check.py](https://github.com/solywsh/wozaixiaoyuancheck/blob/master/Check.py)，除了python环境以外，还需要python的`requests`和`email`库，这个自行百度，每个人环境也不一样。

<a href="https://github.com/solywsh/wozaixiaoyuancheck" class="LinkCard">我在校园打卡脚本仓库</a>

##### 配置脚本

###### 自动提醒邮箱部分

由于打卡成功和失败我需要一个反馈，所以我用了邮箱提醒。

邮箱使用的网易的SMTP，在`Check.py`做出相应的修改。

```python
mail_host = "smtp.163.com"        # SMTP服务器
mail_user = "@163.com" # 用户名为邮箱
mail_pass = ""    # 授权密码，非登录密码 
sender = '@163.com'    # 发件人邮箱
receivers = ['@outlook.com']  # 接收邮件
title = '我在校园自动打卡提醒'  # 邮件主题
```

其中`授权密码`，去163邮箱的设置，有个`POP3/SMTP/IMAP`，打开之后会给你个授权密码。

其他的看注释就是了。

###### 更换token

将Token更换即可，总共需要更换三处，分别为晨检，午检，每日健康打卡。

```python
def HealthCheckIn():
    headers = {
        'content-length' : '296',
        'cookie' : 'SESSION=NGY4ZGYwNGMtZTQ3ZC00ZDRmLTg2MmEtNDRhMDYyOTZlYTAw;path=/;HttpOnly',
        'user-agent' : 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36 MicroMessenger/7.0.9.501 NetType/WIFI MiniProgramEnv/Windows WindowsWechat',
        'content-type' : 'application/x-www-form-urlencoded',
        'token' : '这里换为你的Token',
        'refer' : 'https://servicewechat.com/wxce6d08f781975d91/143/page-frame.html',
        'accept-encoding' : 'gzip, deflate, br'
    }
```

###### 更换地址，和其他信息

现在都还在学校，~~<span style="background-color:#39c5bb">暂时不用变，等回家了再说吧。</span>~~

```python
Hpostdata = {
        'answers' : '["0","36.5"]',#这里36.5为温度
        'latitude' : '34.108216',#这里和下面都是经纬度
        'longitude' : '108.605084',
        'country' : '中国',
        'city' : '西安市',
        'district' : '鄠邑区',
        'province' : '陕西省',
        'township' : '甘亭街道',
        'street' : '东街',
        'areacode' : '610118'# 
    }
```

1月27更新

回家都10来天了，地址请求很简单，在`charles`打开时，进入微信的打卡界面，然后点击一下获取地址，这时charles会自动抓包。

![QQ截图20210127130700.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gn27l7aoioj30qw0t4408.jpg)

###### 更换打卡时间

这里设置的是早上6:30和中午12:00，自己设置就可以了，晨检为6点开始，午检为11点开始，注意需要设置两个连续的秒，因为主函数里是每两秒一个循环。

```python
if time_now == "06:30:10" or time_now == "06:30:11":#不知道是奇数还是偶数
            HealthCheckIn()#健康打卡
            MorningCheck()#晨间
            subject = time.strftime("%Y-%m-%d %H:%M:%S", time.localtime()) + " 晨间打卡/健康"
            
        
if time_now == "11:20:10" or time_now == "11:20:11":
            NoonInspection()#午检
            subject = time.strftime("%Y-%m-%d %H:%M:%S", time.localtime()) + " 午检打卡"
```





#### 运行

然后运行就是了，只要不关闭它，在Token失效之前可以一直用。



### 进阶

#### 宝塔面板下部署脚本(推荐)

如果你有linux服务器或者云服务器，那么就更好了，我们可以24小时不关机时刻运行。它消耗的内存才18.32M。

不管是ubuntu还是centos系统，这里都建议装上宝塔系统。

centos一键安装:

```
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```

其他的系统可以看看下面的官方教程。

<a href="https://www.bt.cn/bbs/thread-19376-1-1.html" class="LinkCard">宝塔Linux面板安装教程</a>

网页进入宝塔面板之后。下载安装。`Python项目管理器 1.9`

![QQ截图20210110214052.png](http://ww1.sinaimg.cn/large/006b3a9lly1gmixk0w5luj31hc0t4wgq.jpg)

安装好了之后，去之前我的场库下载[requirements.txt](https://github.com/solywsh/wozaixiaoyuancheck/blob/master/requirements.txt)，里边记录了需要告诉宝塔安装的python库。

<a href="https://github.com/solywsh/wozaixiaoyuancheck" class="LinkCard">我在校园打卡脚本仓库</a>

准备好之前的`Check.py`和`requirements.txt`，宝塔面板的文件选项卡，找个路径上传。我的是`根目录/home/py/打卡`

![QQ截图20210110214924.png](http://ww1.sinaimg.cn/large/006b3a9lly1gmixsrwvuij31hc0t4410.jpg)

然后再去刚才下载安装的`Python项目管理器 1.9`，添加项目。

![QQ截图20210110215042.png](http://ww1.sinaimg.cn/large/006b3a9lly1gmixu4buuxj30ur0gz0td.jpg)

按照下面的设置就行。

![QQ截图20210110215202.png](http://ww1.sinaimg.cn/large/006b3a9lly1gmixvltp0rj30gv0ixgmd.jpg)

确定之后运行即可。

#### 如果不按照宝塔面板

cd进`check.py`所在的目录

```
nohup python -u check.py > test.log 2>&1 &
```

此方法我也没试过。。。。。。

![IMG_4985.PNG](http://ww1.sinaimg.cn/large/006b3a9lly1gmiy2khqfrj31bb0ix4qq.jpg)