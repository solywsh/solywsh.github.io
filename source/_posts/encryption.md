---

title: 给markdown文章加密
date: 2020-03-26 23:26:42
catalog: true
tags: [blog,工具,加密,分享]
categories: blog

---

<meta name="referrer" content="no-referrer"/>

{% cq %} 前端加密只是个笑话。

鲁迅  {% endcq %}

# 前言

以我目前的能力，加上hexo只是静态网页，加密其实并没有用。

但是，加密好歹能拦住90%的人。

其实加密文档就是给剩下10%的三种人看的：

1.我熟悉的人。

2.联系我要到密码的陌生人。

3.自行破解的人。

以后的加密文档，其实就是给上述三种人观看的。所谓的加密，当个笑话吧。

# 操作

## 具体效果

具体的效果可以移步我的测试文档。

<a href="https://violetwsh.com/2020/03/26/encryption/#more" class="LinkCard">博客文章加密测试文档</a>

## 安装

- `npm install --save hexo-blog-encrypt`
- 或者 `yarn add hexo-blog-encrypt` (需要安装 [Yarn](https://yarnpkg.com/en/))

## 配置

打开站点配置文件`_config.yml`，添加下述文档，启动插件：

```c
encrypt:
    enable: true
```

然后可以在相应的`.md`文档添加对应的字符：

```markdown
---
title: 标题
date: 时间
category: 分类
tags: [blog,工具,加密,分享]   //标签
keywords: 关键词，为检索时使用
password: 密码
abstract: 提醒，文章摘要
---
```

也可以加入：

message: 这个是博客查看时，密码输入框上面的描述性文字。

## 自定义

你可以去修改站点配置文件`_config.yml`从而节省一些时间。

```bash
encrypt:
  enable: true
  default_abstract: 这是一篇加密文章，内容可能是个人情感宣泄或者收费技术内容。如果你确实想看，请Email。
  default_message: 输入密码，查看文章。
```

这样在编写`markdown`时`abstract` ，`message`可以写也可以不写，如果你要在`markdown`文档中写了，就可覆盖站点配置的内容。

## bug

听说这个加密插件会有一些bug，我还没有遇到过，但还是列出:

- 如果你开启了 **字数统计功能** 的话，那么本文的字数会显得比实际值大。
- 加密文章内部分脚本会失效，已知 **代码复制** 失效。

# 链接推荐

hexo官方有专门的主题，插件页面，里边有很多人分享了不错的东西。

## hexo插件

<a href="https://hexo.io/plugins/" class="LinkCard">Plugins</a>

## hexo主题

<a href="https://hexo.io/themes/" class="LinkCard">Themes</a>

当然，你也可以直接去hexo的[官方](https://hexo.io/)页面看看。

# 本文支持

<a href="https://www.jianshu.com/p/44e211829447" class="LinkCard">hexo文章加密</a>

<a href="https://github.com/MikeCoder/hexo-blog-encrypt/blob/master/ReadMe.zh.md" class="LinkCard">hexo-blog-encrypt</a>

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gd7rutuk7sj30ee0a6k6p.jpg"/>