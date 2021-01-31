---
title: HTML5学习笔记part2
date: 2020-05-05 9:45:00
catalog: true
tags: [前端,html,笔记]
categories: html


---



<meta name="referrer" content="no-referrer"/>

<a name="top">顶部标记</a>

# 图像标签

## 常见的图像格式

- JPG
- GIF
- PNG
- BMP（位图）
- ......

## 标签

```html
<img src="path" alt="text" title="text" width="x" height="y"/>
图像标签：<img/>
图像地址：src="path"<!-- 必填 -->
图像替代文字：alt="text"<!-- 图像加载失败时返回的文字/必填 -->
鼠标悬停提示文字：title="text"
图像宽度：width="x"
图像高度：height="y"
```

## src

### 图片地址

- 绝对地址（路径）：从盘符开始`F:\StudyDate\java\HTML\html\study\resources\image\001.png`

- 相对地址（路径/path）：相对路径是指目标相对于当前文件的路径，网页结构设计中多采用这种方法来表示目标的路径。`../study/resources/image/001.png`<span style="background-color:yellow">推荐使用</span>

### 相对路径表示方法

文件所在目录（可不写）：

```
./
```

上一级目录（文件所在父级目录）：

```
../
```

文件所在父级目录的父级目录：

```
../../
```

文件所在的根目录：（可理解为项目内的绝对路径）

```
/
```

## alt

```html
<!-- 正确路径 -->
<img src="../study/resources/image/001.png" alt="马猴小站">
<!-- 错误路径 -->
<img src="../study/resources/image/002.png" alt="马猴小站">
```

正确显示：

![0004.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gehe51wlnpj30qv0t3n0d.jpg)

错误显示：

![0005.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gehe6axdqsj30qh0afjrp.jpg)

# 链接标签

- 文本超链接

- 图像超链接

## 页面间链接

### 语法

```html
<a href="path" target="目标窗口位置">链接文本或图像</a>
链接路径：href="path"<!--必填：跳转到哪个页面-->
链接在哪个窗口打开：target="目标窗口位置"<!--常用值：_self、_blank -->
```

### 两种超链接

```html
<p><a href="002.html">点击我跳转</a></p>
<hr>
<a href="https://www.baidu.com">点击我下载百度</a>
```

效果：

<a href="https://www.baidu.com">点击我下载百度</a>

### 嵌套图片（点击图片跳转网页）

```html
<a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="马猴小站">
</a>
```

点击下面图片尝试

<a href="https://www.baidu.com"> 

<img src="https://i0.hdslb.com/bfs/album/3d359641a69cc34d188ccef2b7871a14a56ae77f.png@518w_1e_1c.png" alt="马猴小站">

</a>

### target

个人理解：其实就是点击链接的时候是否打开新的网页，在这里点名批评谷歌，每次搜索出来的链接都不给新开个页面。

- _bank：新标签中打开

```html
<a href="https://www.baidu.com" target="_blank">点击我下载百度</a>
```

效果：

<a href="https://www.baidu.com" target="_blank">点击我下载百度</a>

加一点优化：

{% btn https://www.baidu.com, 点击下载百度, download fa-lg fa-fw %}

- _self：在自己网页中打开

## 锚链接

- 需要一个标记（锚）
- 跳转到标记

### 同一个页面

```html
<body>
<!-- 使用name作为标记-->
<a name="top">回到顶部</a>
<p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p><p><a href="https://www.bilibili.com/">
    <img src="../study/resources/image/001.png" alt="bilibili">
</a></p>
<a href="#top">回到顶部</a>
</body>
```

效果（点击尝试）：<a href="#top">回到顶部</a>

### 一个页面跳转到另外一个页面

在`001.html`里编辑：

```html
<body>
<a href="002.html#top">回到顶部</a>
</body>
```

在`002.html`里编辑：

```html
<body>
<a name="top">回到顶部</a>
</body>
```

打开`001.html`的网页，点击[回到顶部]()

再比如：`https://violetwsh.com/2020/05/04/HTML5notePart1/#注释和特殊符号`后面的<kbd>#</kbd>+<kbd>一级标题</kbd>

也是锚链接。

## 功能性链接

### 邮件

```html
<a href="mailto:somenoelikeyouwsh@outlook.com">点击骚扰我</a>
```

效果：

<a href="mailto:somenoelikeyouwsh@outlook.com">点击骚扰我</a>

### QQ

在[QQ推广](https://shang.qq.com/v3/widget.html)界面获取代码，复制。

有如下内容：

```html
<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=1228014966&site=qq&menu=yes">
    <img border="0" src="http://wpa.qq.com/pa?p=2:1228014966:51" alt="点击即可骚扰" title="点击即可骚扰"/>
</a>
```

效果：

<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=1228014966&site=qq&menu=yes">
    <img border="0" src="http://wpa.qq.com/pa?p=2:1228014966:51" alt="点击即可骚扰" title="点击即可骚扰"/></a>

## `<a>`标签

转自[W3School](https://www.w3school.com.cn/tags/tag_a.asp)

### 定义和用法

<a> 标签定义超链接，用于从一张页面链接到另一张页面。

<a> 元素最重要的属性是 href 属性，它指示链接的目标。

在所有浏览器中，链接的默认外观是：

- <span style="background-color:blue">未被访问的链接带有下划线而且是蓝色的</span>
- <span style="background-color:purple">已被访问的链接带有下划线而且是紫色的</span>
- <span style="background-color:#ff5c5c">活动链接带有下划线而且是红色的</span>

### 提示和注释

**提示：**如果不使用 href 属性，则不可以使用如下属性：download, hreflang, media, rel, target 以及 type 属性。

**提示：**被链接页面通常显示在当前浏览器窗口中，除非您规定了另一个目标（target 属性）。

**提示：**请使用 CSS 来设置链接的样式。

### 属性

| 属性                                                         | 值                                            | 描述                                                     |
| :----------------------------------------------------------- | :-------------------------------------------- | :------------------------------------------------------- |
| [charset](https://www.w3school.com.cn/tags/att_a_charset.asp) | *char_encoding*                               | **HTML5 中不支持。**规定被链接文档的字符集。             |
| [coords](https://www.w3school.com.cn/tags/att_a_coords.asp)  | *coordinates*                                 | **HTML5 中不支持。**规定链接的坐标。                     |
| [download](https://www.w3school.com.cn/tags/att_a_download.asp) | *filename*                                    | 规定被下载的超链接目标。                                 |
| [href](https://www.w3school.com.cn/tags/att_a_href.asp)      | *URL*                                         | 规定链接指向的页面的 URL。                               |
| [hreflang](https://www.w3school.com.cn/tags/att_a_hreflang.asp) | *language_code*                               | 规定被链接文档的语言。                                   |
| [media](https://www.w3school.com.cn/tags/att_a_media.asp)    | *media_query*                                 | 规定被链接文档是为何种媒介/设备优化的。                  |
| [name](https://www.w3school.com.cn/tags/att_a_name.asp)      | *section_name*                                | **HTML5 中不支持。**规定锚的名称。                       |
| [rel](https://www.w3school.com.cn/tags/att_a_rel.asp)        | *text*                                        | 规定当前文档与被链接文档之间的关系。                     |
| [rev](https://www.w3school.com.cn/tags/att_a_rev.asp)        | *text*                                        | **HTML5 中不支持。**规定被链接文档与当前文档之间的关系。 |
| [shape](https://www.w3school.com.cn/tags/att_a_shape.asp)    | defaultrectcirclepoly                         | **HTML5 中不支持。**规定链接的形状。                     |
| [target](https://www.w3school.com.cn/tags/att_a_target.asp)  | `_blank` `_parent` `_self` `_top` `framename` | 规定在何处打开链接文档。                                 |
| [type](https://www.w3school.com.cn/tags/att_a_type.asp)      | *MIME type*                                   | 规定被链接文档的的 MIME 类型。                           |

# 行元素和块元素

## 块元素

- 无论内容多少，该元素独占一行
- （p、h1、h2、h3......）

## 行（内）元素

- 内容撑开宽度，左右都是行内元素的可以排在一行。
- （a、strong、em）