---
title: HTML5学习笔记part3
date: 2020-05-06 19:45:00
catalog: true
tags: [前端,html,笔记]
categories: html


---



<meta name="referrer" content="no-referrer"/>

# 列表标签

- 什么是列表
  - 列表就是信息资源的一种展示形式。它可以使信息结构化和条理化，并以列表的样式显示出来，以便浏览者能更快捷地获得相应的信息。
- 列表的分类<span style="background-color:yellow">（其实这个就是列表）</span>
  - 无序列表Unordered list
  - 有序列表ordered list
  - 定义列表

## 有序列表

有序列表`（ordered list）`缩写`ol`，应用范围：试卷，问答

```html
大标签：
	<ol></ol>
子标签list：
	<li></li>
表示：
	<ol>
        <li>内容1</li>
        <li>内容2</li>
        <li>内容3</li>
        <li>内容4</li>
	</ol>
```

演示：

```html
<!-- 有序列表 -->
<ol>
    <li>Java</li>
    <li>Python</li>
    <li>运维</li>
    <li>前端</li>
    <li>C/C++</li>
</ol>
```

效果：（直接在本网页显示）

<ol>
    <li>Java</li>
    <li>Python</li>
    <li>运维</li>
    <li>前端</li>
    <li>C/C++</li>
</ol>

## 无序列表

无序列表`（unordered list）`缩写`ul`，应用范围：导航，侧边栏

```html
大标签：
	<ul></ul>
子标签list：
	<li></li>
表示：
	<ul>
        <li>内容1</li>
        <li>内容2</li>
        <li>内容3</li>
        <li>内容4</li>
	</ul>
```

演示：

```html
<!-- 无序列表 -->
<ul>
    <li>Java</li>
    <li>Python</li>
    <li>运维</li>
    <li>前端</li>
    <li>C/C++</li>
</ul>
```

效果：

<ul>
    <li>Java</li>
    <li>Python</li>
    <li>运维</li>
    <li>前端</li>
    <li>C/C++</li>
</ul>

## 自定义列表

应用范围：公司网站底部

```html
dl：自定义标签
子标签：
dt：列表名称
dd：列表内容
```

示例：

```html
<dl>
    <dt>学科</dt>
    <dd>Java</dd>
    <dd>Python</dd>
    <dd>运维</dd>
    <dd>前端</dd>
    <dd>C/C++</dd>
    <dt>位置</dt>
    <dd>四川</dd>
    <dd>西安</dd>
    <dd>北京</dd>
</dl>
```

效果：

<dl>
    <dt>学科</dt>
    <dd>Java</dd>
    <dd>Python</dd>
    <dd>运维</dd>
    <dd>前端</dd>
    <dd>C/C++</dd>
    <dt>位置</dt>
    <dd>四川</dd>
    <dd>西安</dd>
    <dd>北京</dd>
</dl>

# 表格标签

- 为什么使用表格标签
  - 简单通用
  - 结构稳定
- 基本结构
  - 单元格
  - 行
  - 列
  - 跨行
  - 跨列

```html
<!-- 表格 table -->
<!-- 行 tr //rows-->
<!-- 列 td //table data cell-->
<table>
    <tr>
        <td></td>
        <td></td>
    </tr>
</table>

扩展
	增加边框：border属性
<table border="1px">
    <tr>
        <td></td>
        <td></td>
    </tr>
</table>
```

演示：

```html
<table border="1px">
    <tr>
        <td>1-1</td>
        <td>1-2</td>
        <td>1-3</td>
        <td>1-4</td>
        <td>1-5</td>
    </tr>
    <tr>
        <td>2-1</td>
        <td>2-2</td>
        <td>2-3</td>
        <td>2-4</td>
        <td>2-5</td>
    </tr>
    <tr>
        <td>3-1</td>
        <td>3-2</td>
        <td>3-3</td>
        <td>3-4</td>
        <td>3-5</td>
    </tr>
</table>
```

效果：

<table border="1px">
    <tr>
        <td>1-1</td>
        <td>1-2</td>
        <td>1-3</td>
        <td>1-4</td>
        <td>1-5</td>
    </tr>
    <tr>
        <td>2-1</td>
        <td>2-2</td>
        <td>2-3</td>
        <td>2-4</td>
        <td>2-5</td>
    </tr>
    <tr>
        <td>3-1</td>
        <td>3-2</td>
        <td>3-3</td>
        <td>3-4</td>
        <td>3-5</td>
    </tr>
</table>

![006.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej0t1cv4kj305703ta9u.jpg)

## 实现跨列/跨行



```html
跨行：rowspan
	<td rowspan="2">2-1</td>
跨列：colspan
	<td colspan="5">1-1</td>
```

演示：

```html
<table border="1px">
    <tr>
        <!--colspan 跨列-->
        <td colspan="5">1-1</td>
    </tr>
    <tr>
        <!--rowspan 跨行-->
        <td rowspan="2">2-1</td>
        <td>2-2</td>
        <td>2-3</td>
        <td>2-4</td>
        <td>2-5</td>
    </tr>
    <tr>
        <td>3-2</td>
        <td>3-3</td>
        <td>3-4</td>
        <td>3-5</td>
    </tr>
</table>
```

效果：

<table border="1px">
    <tr>
        <!--colspan 跨列-->
        <td colspan="5">1-1</td>
    </tr>
    <tr>
        <!--rowspan 跨行-->
        <td rowspan="2">2-1</td>
        <td>2-2</td>
        <td>2-3</td>
        <td>2-4</td>
        <td>2-5</td>
    </tr>
    <tr>
        <td>3-2</td>
        <td>3-3</td>
        <td>3-4</td>
        <td>3-5</td>
    </tr>
</table>

# 视频和音频（媒体元素）

- 视频元素
  - videos
- 音频元素
  - audio

## 视频元素

```html
<video src="../study/resources/video/dangyang.mp4" controls ><video/>
    controls: 控制条<!--必须-->
    src: 资源路径
    outplay：自动播放
ps：视频的带宽并不是每个人都能接受的吧，带宽好贵的说
```

## 音频元素

```html
<audio src="../study/resources/audio/aimer.flac" controls title="aimer"></audio>
```

