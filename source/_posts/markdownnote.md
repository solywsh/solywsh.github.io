---
title: markdown语法笔记速记（个人用）
date: 2020-05-03 13:00:00
catalog: true
tags: [markdown,md,笔记,语法，share]
categories: markdown
keywords: markdown
---

<meta name="referrer" content="no-referrer"/>

<span style="background-color:#FFF000">平时写markdown的时候有一些总是记不住，故写一篇笔记方便查阅使用，由于只是个人使用，有不理解的地方还请包涵。并且，本文大量参考了https://bestzuo.cn/</span>

<span style="background-color:#4abdac">本文会不定期更新</span>

# 文字部分

## 更改字体、大小、颜色

**[部分参考链接](https://blog.csdn.net/heimu24/article/details/81189700)**

语法

```html
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=red>我是红色</font>
<font color=#008000>我是绿色</font>
<font color=Blue>我是蓝色</font>
<font size=5>我是尺寸</font>
<font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>
```

效果如下：

<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=red>我是红色</font>
<font color=#008000>我是绿色</font>
<font color=Blue>我是蓝色</font>
<font size=5>我是尺寸</font>
<font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>

##　增加按键方块

代码：

```html
<kbd>内容</kbd>
```

效果：

```html
<kbd>F10</kbd>
```

<kbd>F10</kbd>

## 为文字添加背景色

由于 style 标签和标签的 style 属性不被支持，所以这里只能是借助 table, tr, td 等表格标签的 bgcolor 属性来实现背景色。故这里对于文字背景色的设置，只是将那一整行看作一个表格，更改了那个格子的背景色（bgcolor）

语法

```html
table><tr><td bgcolor=yellow>背景色yellow</td></tr></table>
```

效果如下

<table><tr><td bgcolor=yellow>背景色yellow</td></tr></table>

#### 另外一种

```html
<span style="background-color:#FFF000">内容</span>
```

效果如下

<span style="background-color:#FFF000">内容</span>

## 在代码块里

语法：

```diff
​```diff(这是在markdown里调出代码块)
+ 内容
- 内容
```

效果：

```diff
+ 内容
- 内容
```

## markdown扩展

其实markdown本来是支持的，但是在我在渲染的时候并没有把它渲染出来。但如果不上传自己使用的话这个比较方便。

语法：

```
==内容==
```

# 图片部分

<span style="background-color:red">注意</span>

在引用图片时注意在文章开头添加以下代码：

```html
<meta name="referrer" content="no-referrer"/>
```

以防止图片加载不出。

## 设置图片大小

### 设置设置图片百分比

语法

```html
<img src="图片链接" width="50%" height="50%">
```

效果如下

<img src="https://i0.hdslb.com/bfs/album/3d359641a69cc34d188ccef2b7871a14a56ae77f.png@518w_1e_1c.png" width="50%" height="50%">

### 设置图片大小

语法

```html
<img src="图片链接" width="350" height="350" >
```

效果如下

<img src="https://i0.hdslb.com/bfs/album/3d359641a69cc34d188ccef2b7871a14a56ae77f.png@518w_1e_1c.png" width="350" height="350" >

### 设置图片居中

语法

`center,left,left`

```
<div align=right><img src="图片链接" width="50%" height="50%"></div>
```

效果如下

<div align=right><img src="https://i0.hdslb.com/bfs/album/3d359641a69cc34d188ccef2b7871a14a56ae77f.png@518w_1e_1c.png" width="50%" height="50%"></div>

# 选项卡

[参考](https://bestzuo.cn/posts/3147047336.html)

## 语法

```
{% tabs 选项卡, 2 %}
<!-- tab -->
**这是选项卡 1** 呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈……
<!-- endtab -->
<!-- tab -->
**这是选项卡 2**
<!-- endtab -->
<!-- tab -->
**这是选项卡 3** 哇，你找到我了！φ(≧ω≦*)♪～
<!-- endtab -->
{% endtabs %}
```

## 效果

{% tabs 选项卡, 2 %}
<!-- tab -->
**这是选项卡 1** 呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈……
<!-- endtab -->
<!-- tab -->
**这是选项卡 2**
<!-- endtab -->
<!-- tab -->
**这是选项卡 3** 哇，你找到我了！φ(≧ω≦*)♪～
<!-- endtab -->
{% endtabs %}

然后上面源码中`, 2`表示一开始在第二个选项卡，非必须，若数值为`-1`则隐藏选项卡内容。更多用法请查看[这个页面](https://almostover.ru/2016-01/hexo-theme-next-test/#Tab-tag-test)。

# 外部（引用）链接

## markdown

语法：

```markdown
[文字说明](链接地址)
```

效果：

[马猴小站](https://violetwsh.com)

## 扩展部分

由于我加了类似于知乎卡片一个功能，外部链接还可以更美观一点。

语法：

```html
<a href="网址" class="LinkCard">说明文字</a>
```

效果：

<a href="https://violetwsh.com" class="LinkCard">马猴小站</a>

```html
<a href="https://violetwsh.com" class="LinkCard">马猴小站</a>
```

### 附

链接的图片可以更改，替换`.\bolg\themes\next\source\images`下的`linkcard.png`即可。但名字和格式必须一样。

# 引用文字

> <span style="background-color:red">注意</span>
>
> 使用Bootstrap Callout的标签会出现各种bug，比如一级二级三级标题无法显示等等。
>
> 故，使用noto的标签。

详情请看之前写的一篇文章：

<a href="https://violetwsh.com/2020/03/25/TitleProblem/#more" class="LinkCard">Bootstrap Callout</a>

语法：

```
{% note 颜色 %}
内容
{% endnote %}
```

颜色可以是：

- default 无色

- primary 紫色

- success 绿色

- info 蓝色

- warning 黄色

- danger 红色

- 无图

<span style="background-color:red">注意</span>

不能这样写：（会出bug）

```
- 无图
{% note info no-icon %}
没有图标的note标签
{% code %}
```



完整语法：

```
{% note [class] [no-icon] %}
内容
{% endnote %}

其中：[class] [no-icon] 都可以用相应的修改，也可以不写
[class]   : default | primary | success | info | warning | danger.
[no-icon] : Disable icon in note.
```

效果：

```
{% note danger %}
内容
{% endnote %}
```

{% note danger %}
内容
{% endnote %}

# noto标签

[本文参考](https://bestzuo.cn/posts/3147047336.html)

## note标签中插入有序无序列表

```
{% note default %}
在note中放入无序、有序列表
* ul
* ul
* ul

1. ol
2. ol
3. ol
{% endnote %}
```

{% note default %}
在note中放入无序、有序列表
* ul
* ul
* ul

1. ol
2. ol
3. ol

{% endnote %}

## note标签中插入表格

```
{% note default %}
| 1 | 2 |
| - | - |
| 3 | 4 |
| 5 | 6 |
| 7 | 8 |
{% endnote %}
```

{% note default %}

| 1    | 2    |
| ---- | ---- |
| 3    | 4    |
| 5    | 6    |
| 7    | 8    |

{% endnote %}

## note标签的html使用

><span style="background-color:#FFF000">博主原文</span>
>
>在主题配置文件`_config.yml`里有一个关于这个的配置，但官方文档没有提供 HTML 的使用方式，个人认为这种方式更简单，也不会产生一些奇怪的显示 bugs……

```
<div class="note default"><p>default</p></div>
```

<div class="note default"><p>default</p></div>

```
<div class="note primary"><p>primary</p></div>
```

<div class="note primary"><p>primary</p></div>

```
<div class="note success"><p>success</p></div>
```

<div class="note success"><p>success</p></div>

```
<div class="note info"><p>info</p></div>
```

<div class="note info"><p>info</p></div>

```
<div class="note warning"><p>warning</p></div>
```

<div class="note warning"><p>warning</p></div>

```
<div class="note danger"><p>danger</p></div>
```

<div class="note danger"><p>danger</p></div>

```
<div class="note danger no-icon"><p>danger no-icon</p></div>
```

<div class="note danger no-icon"><p>danger no-icon</p></div>

# 主题自带FontAwesome图标

[主题自带FontAwesome图标](https://bestzuo.cn/posts/3147047336.html#主题自带FontAwesome图标)

```
1. <i class="fa fa-pencil"></i> 支持 Markdown
   <i>Hexo 支持 GitHub Flavored Markdown 的所有功能，甚至可以整合 Octopress 的大多数插件。</i>
2. <i class="fa fa-cloud-upload"></i> 一件部署
   <i>只需一条指令即可部署到 GitHub Pages，或其他网站。</i>
3. <i class="fa fa-cog"></i> 丰富的插件
   <i>Hexo 拥有强大的插件系统，安装插件可以让 Hexo 支持 Jade，CoffeeScript。</i>
   采用的是 Font Awesome 的图标，下面给出一些简单的使用例子，更多请查看官网的使用示例。
```

 效果：

<i class="fa fa-pencil"></i> 支持 Markdown
<i>Hexo 支持 GitHub Flavored Markdown 的所有功能，甚至可以整合 Octopress 的大多数插件。</i>

<i class="fa fa-cloud-upload"></i> 一件部署
<i>只需一条指令即可部署到 GitHub Pages，或其他网站。</i>

<i class="fa fa-cog"></i> 丰富的插件
<i>Hexo 拥有强大的插件系统，安装插件可以让 Hexo 支持 Jade，CoffeeScript。</i>
采用的是 Font Awesome 的图标，下面给出一些简单的使用例子，更多请查看官网的使用示例。

其他：

```
- <i class="fa fa-pencil"></i> 铅笔
- <i class="fa fa-cloud-upload"></i> 上传
- <i class="fa fa-download"></i> 下载
```

- <i class="fa fa-pencil"></i> 铅笔
- <i class="fa fa-cloud-upload"></i> 上传
- <i class="fa fa-download"></i> 下载

```
- <i class="fa fa-download"></i> 下载
- <i class="fa fa-download fa-lg"></i> 下载变大 33%
- <i class="fa fa-download fa-2x"></i> 下载两倍大
```

- <i class="fa fa-download"></i> 下载
- <i class="fa fa-download fa-lg"></i> 下载变大 33%
- <i class="fa fa-download fa-2x"></i> 下载两倍大

# 文本居中引用

{% cq %}
鲁迅说：
我没说过
{% endcq %}

```
{% cq %}
鲁迅说：
我没说过
{% endcq %}
```

# 主题自带label标签

[参考](https://bestzuo.cn/posts/3147047336.html)

>注意这个有一个BUG，千万不要把这个放到段首。。。

{% label default@文字 %}

```
{% label default@文字 %}
```

{% label primary@文字 %}

```
{% label primary@文字 %}
```

{% label success@文字 %}

```
{% label primary@文字 %}
```

{% label info@文字 %}

```
{% label info@文字 %}
```

{% label warning@文字 %}

```
{% label warning@文字 %}
```

{% label danger@文字 %}

```
{% label danger@文字 %}
```

# 主题自带样式按钮

源码

```
{% btn https://www.baidu.com, 点击下载百度, download fa-lg fa-fw %}
```

{% btn https://www.baidu.com, 点击下载百度, download fa-lg fa-fw %}

关于按钮的更多使用可以前往[这个页面](https://almostover.ru/2016-01/hexo-theme-next-test/#Button-tag-test)查看。

# 加密

在md开头加上对应文字即可：

```diff
---
title: 标题
date: 时间
category: 分类
tags: [blog,工具,加密,分享]   //标签
keywords: 关键词，为检索时使用
+ password: 密码
abstract: 提醒，文章摘要
---
```

详情请看：

<a href="https://violetwsh.com/2020/03/26/encryption/#more" class="LinkCard">给markdown文章加密</a>

效果：

<a href="https://violetwsh.com/2020/03/26/encryptionTest/#more" class="LinkCard">博客文章加密测试文档</a>

# 嵌入视频

打开B站相应视频的网页，点击分享，复制嵌入代码

在编辑.md文档时，插入以下代码(注意不要引用代码块)，然后替换掉相应的内容即可

```html
{% raw %}

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    在此处粘贴（并去掉 ></iframe>） style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"> </iframe>
</div>

{% endraw %}
```

详情看：

<a href="https://violetwsh.com/2020/03/22/videotest/#more" class="LinkCard">视频嵌入测试/分享</a>

