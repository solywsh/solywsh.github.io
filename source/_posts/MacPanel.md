---
title: 转载：Hexo NexT主题代码块美化
date: 2020-05-01 10:32:00
catalog: true
tags: [blog,,hexo搭建,share]
categories: hexo
keywords: hexo
---



前不久看见有人做出了mac风格的代码块，51劳动节闲下来之余，也就去查找了一番，找到如下比较适合的操作方式：

原文链接：

<a href="http://wiki.johnhao.tech/Hexo%E4%B9%8BNexT%E4%B8%BB%E9%A2%98%E4%BB%A3%E7%A0%81%E5%9D%97MacPanel%E7%89%B9%E6%95%88%E9%85%8D%E7%BD%AE/" class="LinkCard">Hexo之NexT主题代码块MacPanel特效配置</a>

# 正文

在NexT主题下的scripts目录中创建events.js

```css
var exec = require('child_process').exec;

hexo.on('new', function(data){
    exec('open -a MacDown ' + data.path);
});
```

在NexT主题下的scripts目录中创建codeblock.js

```css
var attributes = [
  'autocomplete="off"',
  'autocorrect="off"',
  'autocapitalize="off"',
  'spellcheck="false"',
  'contenteditable="true"'
]

var attributesStr = attributes.join(' ')

hexo.extend.filter.register('after_post_render', function (data) {
  while (/<figure class="highlight ([a-zA-Z]+)">.*?<\/figure>/.test(data.content)) {
    data.content = data.content.replace(/<figure class="highlight ([a-zA-Z]+)">.*?<\/figure>/, function () {
      var language = RegExp.$1 || 'plain'
      var lastMatch = RegExp.lastMatch
      lastMatch = lastMatch.replace(/<figure class="highlight /, '<figure class="iseeu highlight /')
      return '<div class="highlight-wrap"' + attributesStr + 'data-rel="' + language.toUpperCase() + '">' + lastMatch + '</div>'
    })
  }
  return data
})
```

在 themes/next/source/css/_common/components/highlight/highlight.styl 的基础上调整了下样式，包裹上一层类 mac Panel 的效果。

<span style="background-color:#FFF000">注： 这里不用删除原来highlight.styl里边的内容，只需要在末尾添加下面代码即可</span>

```css
.highlight-wrap[data-rel] {
  position: relative;
  overflow: hidden;
  border-radius: 5px;
  box-shadow: 0 10px 30px 0px rgba(0,0,0,0.4);
  margin: 35px 0;
  ::-webkit-scrollbar {
    height: 10px;
  }

  ::-webkit-scrollbar-track {
      -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
      border-radius: 10px;
  }

  ::-webkit-scrollbar-thumb {
      border-radius: 10px;
      -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.5);
  }
  &::before {
    color: white;
    content: attr(data-rel);
    height: 38px;
    line-height: 38px;
    background: #21252b;
    color: #fff;
    font-size: 16px;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    font-family: 'Source Sans Pro', sans-serif;
    font-weight: bold;
    padding: 0px 80px;
    text-indent: 15px;
    float: left;
  }
  &::after {
    content: " ";
    position: absolute;
    -webkit-border-radius: 50%;
    border-radius: 50%;
    background: #fc625d;
    width: 12px;
    height: 12px;
    top: 0;
    left: 20px;
    margin-top: 13px;
    -webkit-box-shadow: 20px 0px #fdbc40, 40px 0px #35cd4b;
    box-shadow: 20px 0px #fdbc40, 40px 0px #35cd4b;
    z-index: 3;
  }
}
```

在highlight.styl中找到如下部分代码，修改margin为36px 0 0 0：

```diff
$code-block {
  overflow: auto;
-  margin: 20px 0;
+  margin: 36px 0 0 0;
  padding: 0;
  font-size $code-font-size;
  color: $highlight-foreground;
  background: $highlight-background;
  line-height: $line-height-code-block;
}
```

最后在主题中将高亮代码变为：night eighties

```yaml
highlight_theme: night eighties
```

