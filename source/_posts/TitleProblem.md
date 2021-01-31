---

title: Bootstrap Callout导致hexo博客.md文档标题无法正常显示的办法
date: 2020-03-25 16:26:42
catalog: true
tags: [blog,,problem,分享]
categories: problem
keywords: blog
---

<meta name="referrer" content="no-referrer"/>

我在写第六单元的[作业](https://violetwsh.com/2020/03/16/2020-03-16-homework/#more)时，内容写在了.md(markdown)文档里，出于测试的原因，使用了很多新添加的功能，导致了我的部分一级，二级，三级标题在渲染后无法正常显示。再删除Bootstrap Callout相关标签之后居然就恢复正常了。

.md的标题分级语法是：

# # 一级标题

## ## 二级标题

### ### 三级标题

#### #### 四级标题

**但是**，我在hexo 的 next主题官方看见了Bootstrap Callout标签用法。

<a href="http://theme-next.iissnan.com/tag-plugins.html" class="LinkCard">Bootstrap Callout标签官方说明</a>

顺便一提，这个类似于知乎卡片式的链接也是新添加的功能，引用语法是：

```html
<a href="网址" class="LinkCard">说明文字</a>
```

具体怎么配置可以看下面链接的第12点

<a href="https://www.liaofuzhan.com/posts/2114475547.html" class="LinkCard">Hexo NexT 主题美化2.0</a>

本来我在引用某段文字时，应该这样使用：

> 这是一段文字

语法是，在文字前加大于号`>`

```
>文字
```

而Bootstrap Callout语法是

```
{% note class_name %} 内容 {% endnote %}
```

class_name可以是：

- `default`
- `primary`
- `success`
- `info`
- `warning`
- `danger`

例如：

{% note default %} default {% endnote %}

{% note primary %} primary {% endnote %}

{% note success %} success {% endnote %}

{% note info %} info {% endnote %}

{% note warning %} warning {% endnote %}

{% note danger %} danger {% endnote %}

使用这种方法比较美观，但是，很多`hexo`主题会出现bug（比如我的标题渲染时就会出现问题），那么问题来了，如果想要使用相似的标签，但是又不想出bug怎么办？

其实`Next`也自带了类似的标签。（我就搞不懂官方的说明文档为什么没有这个，而是Bootstrap Callout这种容易出bug的）

我们需要在`Next`主题`_config.xml`中设置一下功能开关，有些默认是开的，有些默认是关的：

```
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```

语法

```
{% note [class] [no-icon] %}
这是一段文字
{% endnote %}

其中：[class] [no-icon] 都可以用相应的修改，也可以不写
[class]   : default | primary | success | info | warning | danger.
[no-icon] : Disable icon in note.
```

测试

{% note danger %}
测试
{% endnote %}

代码

```
{% note danger %}
测试
{% endnote %}
```



换了标签之后，就没那么容易出bug了。

本文内容支持：（里边写了很多关于markdown的语法知识，可以去看看）

<a href="https://bestzuo.cn/posts/3147047336.html" class="LinkCard">hexo博客Next主题进阶写作技巧</a>



反正没人看，偷偷放个图应该不会被发现吧。。。。。。



<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gd648ee1scj30ee0kg41i.jpg"/>