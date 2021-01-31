---

title: 视频嵌入测试/分享--瘟疫医生
date: 2020-03-22 12:00:00
catalog: true
tags: [个人,test,video，share]
categories: videos
keywords: 视频
---

# 视频测试



<!--more-->

{% raw %}

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=64768491&cid=112430226&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"> </iframe>
</div>


{% endraw %}

# 嵌入方法

打开B站相应视频的网页，点击分享，复制嵌入代码

在编辑.md文档时，插入以下代码(注意不要引用代码块)，然后替换掉相应的内容即可

```html
{% raw %}

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    在此处粘贴（并去掉 </iframe>） style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"> </iframe>
</div>

{% endraw %}
```

## 4.30 更新

在嵌入方法中，有一个并去掉 <span style="background-color:#FFF000">并去掉 </iframe></span>，此处有误，改为 <span style="background-color:#FFF000">并去掉></iframe></span>

感谢[Yinlei](http://ptdexww.com/)指正~~~

## 举例

```html
{% raw %}

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=64768491&cid=112430226&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"> </iframe>
</div>

{% endraw %}
```

# 视频分享（3.24）

{% raw %}

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;">
    <iframe src="//player.bilibili.com/player.html?aid=98219293&bvid=BV1vE411w73j&cid=168252030&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; height: 100%; left: 0; top: 0;"> </iframe>
</div>


{% endraw %}