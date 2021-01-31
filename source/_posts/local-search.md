---

title: hexo next主题下local-search无法点击的一种解决办法
date: 2020-05-01 19:26:42
catalog: true
tags: [blog,search,problem,分享]
categories: problem
---



<meta name="referrer" content="no-referrer"/>

文章多了起来之后，有些情况查阅起来很不是方便，所以想到hexo的Next主题集成了本地搜索插件，经过一番查询之后也实现了此功能，且操作起来简单。

这里简单提一下local-search的部署流程：

- 安装 `hexo-generator-searchdb`，在git bash执行以下命令：

```
 npm install hexo-generator-searchdb --save
```

- 然后编辑站点配置文件，新增以下内容到末尾就好

```yaml
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

- 编辑主题配置文件，启用本地搜索功能

```yaml
# Local search
local_search:
  enable: true
```

- 最后hexo clean, hexo g ,hexo s一套操作就可以。

<span style="background-color:#FFF000">但是</span>

我的博客出现问题了，当我点击搜索按钮输入关键字之后，点击链接，然后。。。。然后就没有然后了。

![search.gif](http://ww1.sinaimg.cn/large/006b3a9lgy1ged4mbt85wg30hs0a0wus.gif)



<span style="background-color:#198fdc">也就是说，它并没有跳转到我想要的页面去。</span>

怎么办？我又不会HTML和CSS。

没关系，F12帮你搞定。

在`hexo s --debug`(当然hexo s也是可以的)进入http://localhost:4000/ 之后，我们按F12调出浏览器的开发者模式。

利用在开发者模式中`页面中选择一个元素进行检查`的功能，选择搜索相关的元素。

![RFKIUV5_47QQR8JBRBB4@~9.png](http://ww1.sinaimg.cn/large/006b3a9lgy1ged4vpx0gyj31hc0t4apy.jpg)

在样式栏看到如下代码：

```css
.local-search-pop-overlay {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 2080;
    background-color: rgba(0,0,0,0.3);
}
```

显然这是css语言，但是问题来了，我没学过啊。

办法很简单，挨个挨个给注释掉试试就可以：（在浏览器上可以直接勾选来控制是否注释掉）

于是我发现将它注释掉之后，搜索正常使用了：

```css
 z-index: 2080;
```

查阅资料：

z-index 属性指定一个元素的堆叠顺序。

拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。

**注意：** z-index 进行定位元素(position:absolute, position:relative, or position:fixed)。

| 默认值：          | auto                      |
| :---------------- | ------------------------- |
| 继承：            | no                        |
| 版本：            | CSS2                      |
| JavaScript 语法： | *object*.style.zIndex="1" |

------

## 浏览器支持

表格中的数字表示支持该属性的第一个浏览器版本号。

| 属性    | chrome | egde | firefox | sifari | Opera |
| :------ | ------ | ---- | ------- | ------ | ----- |
| z-index | 1.0    | 4.0  | 3.0     | 1.0    | 4.0   |

------

## 属性值

| 值       | 描述                                    |
| :------- | :-------------------------------------- |
| auto     | 默认。堆叠顺序与父元素相等。            |
| *number* | 设置元素的堆叠顺序。                    |
| inherit  | 规定应该从父元素继承 z-index 属性的值。 |

<span style="background-color:#198fdc">显然这里堆叠顺序出现了问题，可能是我在部署其他的功能时，与它造成了冲突。</span>

本来注释掉了就可以，但是我在修改参数时，发现浏览器贴心的给了我`auto`，`inherit`，`initial`以及`unset`四个选项，不会CSS的我（看来我该学学前端了），当然是选择`auto`。

当然，在浏览器修改是没有的，毕竟不是永久，于是我们得想办法吧它保存下来。

在`.\bolg\themes\next\source\css\_custom`里有一个`custom.styl`的`css`文件，这是官方留给我们自行修改的，在我不会CSS语法的时候，在开发者模式下进行了一些样式上的修改可以直接复制到这里。比如背景图片，侧栏的颜色什么的。

详细的操作可以看下面的链接：

<a href="https://yangbingdong.com/2017/build-blog-hexo-advanced/#定位元素" class="LinkCard">定位元素</a>

但，这一次不行。因为local-search有一个独立的CSS文件，所以直接在资源管理器搜索`localsearch`，找到它的样式文件。

![QQ截图20200501190208.png](http://ww1.sinaimg.cn/large/006b3a9lgy1ged5ky9h0nj31hc0t476r.jpg)

我们看到一个`localsearch.styl`文件，打开它，搜索<span style="background-color:#198fdc">z-index: 2080</span>，将2080改为`auto`（其实将它删除之后就是默认值auto了。。。。。。。。）

保存，clean，再渲染，就会发现搜索功能能用了。

![search001.gif](http://ww1.sinaimg.cn/large/006b3a9lgy1ged5u8tnpjg30hs0a0e1t.gif)