---
title: git学习笔记part1-基础篇
date: 2020-05-05 16:15:00
catalog: true
tags: [git,笔记]
categories: git
---

<meta name="referrer" content="no-referrer"/>

# Git导图

在我的微信公众号`magic码上来`回复`git`即可下载图片的PDF格式

<img src="http://ww1.sinaimg.cn/large/006b3a9lgy1gehnm05n6zj32eo1o01kx.jpg"/>



### 学习网站

有这个，就够了，在游戏中学习git的知识。

<span style="background-color:#ff5c5c">声明：以下笔记内容均来自这个网站</span>

<a href="https://learngitbranching.js.org/?locale=zh_CN" class="LinkCard">learngitbranching</a>

# 基础篇-循序渐进地介绍 Git 主要命令

## git Commit

- Git 仓库中的提交记录保存的是你的目录下所有文件的快照，**就像是把整个目录复制，然后再粘贴一样，但比复制粘贴优雅许多！**

- Git 希望提交记录尽可能地轻量，因此在你每次进行提交时，它并不会盲目地复制整个目录。条件允许的情况下，它会将当前版本与仓库中的上一个版本进行对比，并把所有的差异打包到一起作为一个提交记录。

- **Git 还保存了提交的历史记录。**这也是为什么大多数提交记录的上面都有父节点的原因。对于项目组的成员来说，维护提交历史对大家都有好处。

- 提交记录非常轻量，可以快速地在这些提交记录之间切换！

## Git Branch

- Git 的分支也非常轻量。它们只是简单地指向某个提交纪录 —— 仅此而已。所以许多 Git 爱好者传颂：<span style="background-color:#ff5c5c">早建分支！多用分支！</span>

- 这是因为即使创建再多分的支也不会造成储存或内存上的开销，并且按逻辑分解工作到不同的分支要比维护那些特别臃肿的分支简单多了。

- 在将分支和提交记录结合起来后，我们会看到两者如何协作。现在只要记住使用分支其实就相当于在说：<span style="background-color:yellow">“我想基于这个提交以及它所有的父提交进行新的工作。”</span>

### 步骤

在<kbd>C0</kbd>(master*)的基础上创建名为`newImage`的分支<kbd>C1</kbd>

```
git branch newImage
```

![001.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gehp5vm92mj30bv0b20sn.jpg)

提交，提交之后新的分支相当于<kbd>另存为</kbd>，但是操作时还是修改原来的<kbd>C0</kbd>，只不过<kbd>C0</kbd>变成了<kbd>C2</kbd>

```
git commit
```

![002.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gehp80r25dj30bv0b2weh.jpg)

回到新的分支上：

```
git checkout <name>
```

命令：

```
git checkout newImage; git commit
```

现在，切换到了`newImage`<kbd>C2</kbd>

![003.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gehph0xjgfj30bx0b23yi.jpg)

## Git Merge

分支与合并

- 新建一个分支，在其上开发某个新功能，开发完成后再合并回主线。

- git merge：在 Git 中合并两个分支时会产生一个特殊的提交记录，它有两个父节点。翻译成自然语言相当于：“我要把这两个父节点本身及它们所有的祖先都包含进来。”

在<kbd>C3</kbd>`master *`分支时，将<kbd>C2</kbd>`bugFix`分支合并到<kbd>C3</kbd>`master *`里去。

![004.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei0cvyc9lj30bv0b274d.jpg)

输入命令把 `bugFix` 合并到 `master` 里

```
git merge bugFix
```

![005.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei0fvqpw3j30bv0b2dfz.jpg)

首先，`master` 现在指向了一个拥有两个父节点的提交记录。假如从 `master` 开始沿着箭头向上看，在到达起点的路上会经过所有的提交记录。这意味着 `master` 包含了对代码库的所有修改。

还有，看见各个提交记录的颜色变化了吗？为了帮助学习理解，我引入了颜色搭配。每个分支都有不同的颜色，而每个提交记录的颜色是所有包含该提交记录的分支的颜色混合之后的颜色。

所以，`master` 分支的颜色被混入到所有的提交记录，但 `bugFix` 没有。

<hr/>

再把 `master` 分支合并到 `bugFix`：



![006.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei0rwzsvpj30bv0b3dfz.jpg)

```
git checkout bugFix; git merge master
```

![007.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei0u2xwj7j30bv0b13yl.jpg)

因为 `master` 继承自 `bugFix`，Git 什么都不用做，只是简单地把 `bugFix` 移动到 `master` 所指向的那个提交记录。

现在所有提交记录的颜色都一样了，这表明每一个分支都包含了代码库的所有修改！大功告成！

### 通关步骤

要想通过这一关，需要以下几步：<span style="background-color:yellow">建议去网站实际操作，非常有意思</span>

![008.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei0yyznmjj30dx0ir3yv.jpg)

- 创建新分支 `bugFix` //branch
- 用 `git checkout bugFix` 命令切换到该分支
- 提交一次
- 用 `git checkout master` 切换回 `master`
- 再提交一次
- 用 `git merge` 把 `bugFix` 合并到 `master`
- 你随时都可以用“objective”命令来打开这个对话框！*

## Git Rebase

- 第二种合并分支的方法是 `git rebase`。Rebase 实际上就是取出一系列的提交记录，“复制”它们，然后在另外一个地方逐个的放下去。

- Rebase 的优势就是可以创造更线性的提交历史，这听上去有些难以理解。如果只允许使用 Rebase 的话，代码库的提交历史将会变得异常清晰。

准备两个分支；注意当前所在的分支是 bugFix（星号标识的是当前分支）

我们想要把 bugFix 分支里的工作直接移到 master 分支上。移动以后会使得两个分支的功能看起来像是按顺序开发，但实际上它们是并行开发的。

咱们这次用 `git rebase` 实现此目标

![009.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei1jmb5y4j30bw0b3glp.jpg)

```
git rebase mater
```

![010.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei1m5woxsj30bw0b2dfy.jpg)

现在 bugFix 分支上的工作在 master 的最顶端，同时我们也得到了一个更线性的提交序列。

注意，提交记录 C3 依然存在（树上那个半透明的节点），而 C3' 是我们 Rebase 到 master 分支上的 C3 的副本。

现在唯一的问题就是 master 还没有更新。

更新master分支：

- 切换到 `master` 上。把它 rebase 到 `bugFix`分支上

```
git rebase bugFix
```

![011.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei1s1l3prj30bv0b2t8s.jpg)

好了！由于 `bugFix` 继承自 `master`，所以 Git 只是简单的把 `master` 分支的引用向前移动了一下而已

### 通关步骤

要完成此关，执行以下操作：

![012.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei1tnfjhdj30dy0jsaab.jpg)

- 新建并切换到 `bugFix` 分支

```
git branch bugFix; git checkout bugFix
```

- 提交一次

```
git commit
```

- 切换回 master 分支再提交一次

```
git checkout master; git commit
```

![013.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gei1z6ykfvj308a0a1mx8.jpg)

- 再次切换到 bugFix 分支，rebase 到 master 上

```
git checkout bugFix; git rebase master
```

过关