---
title: git学习笔记part2-高级篇
date: 2020-05-16 16:15:00
catalog: true
tags: [git,笔记]
categories: git
---

<meta name="referrer" content="no-referrer"/>

# 分离 HEAD

在提交树上移动：在接触 Git 更高级功能之前，我们有必要先学习在你项目的提交树上前后移动的几种方法。

## HEAD

- HEAD 是一个对当前检出记录的符号引用 —— <span style="background-color:yellow">也就是指向你正在其基础上进行工作的提交记录。</span>
- HEAD 总是指向当前分支上最近一次提交记录。大多数修改提交树的 Git 命令都是从改变 HEAD 的指向开始的。
- HEAD 通常情况下是指向分支名的（如 bugFix）。在你提交时，改变了 bugFix 的状态，这一变化通过 HEAD 变得可见。



![014.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej5jxtpphj30bw0b2mx2.jpg)

```
git checkout C1; git checkout master; git commit;git checkout C1;
```

![015.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej5q1cb1nj30bw0b2q2x.jpg)

> 看到了吗？ HEAD 指向了 `master`，随着提交向前移动。
>
> （译者注：实际这些命令并不是真的在查看 HEAD 指向，看下一屏就了解了。如果想看 HEAD 指向，可以通过 `cat .git/HEAD` 查看， 如果 HEAD 指向的是一个引用，还可以用 `git symbolic-ref HEAD` 查看它的指向。但是该程序不支持这两个命令）（怎么译者注都来了）





## 分离的 HEAD

分离的 HEAD 就是让其指向了<span style="background-color:#ff5c5c">某个具体的提交记录而不是分支名</span>。在命令执行之前的状态如下所示：

HEAD -> master -> C1

HEAD 指向 master， master 指向 C1

![016.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej5rxvo46j30bx0b4mx2.jpg)

```html
git checkout C1
```

![017.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej5u4dt0wj30bv0b4aa0.jpg)

现在变成了

HEAD -> C1

## 通关记录

想完成此关，从 `bugFix` 分支中分离出 HEAD 并让其指向一个提交记录。

通过哈希值指定提交记录。每个提交记录的哈希值显示在代表提交记录的圆圈中。

![018.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej5vqnxj8j30dw0js3yt.jpg)

```
git checkout C4
```

# 相对引用1（^）

通过指定提交记录哈希值的方式在 Git 中移动不太方便。在实际应用时，并没有可视化提交树供你参考，所以你就不得不用 `git log` 来查查看提交记录的哈希值。

并且哈希值在真实的 Git 世界中也会更长（译者注：基于 SHA-1，共 40 位）。例如前一关的介绍中的提交记录的哈希值可能是 `fed2da64c0efc5293610bdd892f82a58e8cbc5d8`。舌头都快打结了吧...

比较令人欣慰的是，Git 对哈希的处理很智能。你只需要提供能够唯一标识提交记录的前几个字符即可。因此我可以仅输入`fed2` 而不是上面的一长串字符。

正如前面所说，通过哈希值指定提交记录很不方便，所以 Git 引入了相对引用。这个就很厉害了!

使用相对引用的话，你就可以从一个易于记忆的地方（比如 `bugFix` 分支或 `HEAD`）开始计算。

相对引用非常给力，这里我介绍两个简单的用法：

- 使用 `^` 向上移动 1 个提交记录
- <span style="background-color:yellow">使用 `~<num>` 向上移动多个提交记录，如 `~3`</span>

首先看看操作符 (^)。把这个符号加在引用名称的后面，表示让 Git 寻找指定提交记录的父提交。

所以 `master^` 相当于“`master` 的父节点”。

`master^^` 是 `master` 的第二个父节点

现在切换到 master 的父节点

![019.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej67ioq4xj30bw0b40so.jpg)

```
git checkout master^
```

搞定。这种方式是不是比输入哈希值方便多了？！

你也可以将 `HEAD` 作为相对引用的参照。下面咱们就用 `HEAD` 在提交树中向上移动几次。

![021.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej6cw1isjj30bx0b3dft.jpg)

```
git checkout C3; git checkout HEAD^; git checkout HEAD^; git checkout HEAD^;
```

![022.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej6emq5ukj30bw0b074b.jpg)

我们可以一直使用 `HEAD^` 向上移动。

## 通关记录

要完成此关，切换到 `bugFix` 的父节点。这会进入分离 `HEAD` 状态。

如果你愿意的话，使用哈希值也可以过关，但请尽量使用相对引用！

![023.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej6g8j40pj308m0dkt8u.jpg)

到

![024.png](http://ww1.sinaimg.cn/large/006b3a9lgy1gej6h2kwrtj30dy0jsjro.jpg)

解法1：

```
git checkout bugFix; git checkout HEAD^
```

或者

```
git checkout C4; git checkout HEAD^
```

解法2：`git checkout C3`

~~<span style="background-color:yellow">今晚不写了，肩膀疼，想睡觉</span>~~

<span style="background-color:yellow">5.16 继续</span>

# 相对引用2（~）

### “~”操作符

如果你想在提交树中向上移动很多步的话，敲那么多 `^` 貌似也挺烦人的，Git 当然也考虑到了这一点，于是又引入了操作符 `~`。

该操作符后面可以跟一个数字（可选，不跟数字时与 `^` 相同，向上移动一次），指定向上移动多少次。

<hr/>

用 `~` 一次后退四步。



![025.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geua7pmq60j30bw0b2mx6.jpg)

```
git checkout HEAD~4
```

![026.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geua9a6m3lj30bu0b2aa4.jpg)

## 强制修改分支位置

你现在是相对引用的专家了，现在用它来做点实际事情。

我使用相对引用最多的就是移动分支。可以直接使用 `-f` 选项让分支指向另一个提交。例如:

```
git branch -f master HEAD~3
```

上面的命令会将 master 分支强制指向 HEAD 的第 3 级父提交。

> <span style="background-color:yellow">其实读到这里我并没有懂作者的意思，查看了别人的提示后，我自己的理解是，`-f`命令可以强制移动一个分支到指定的位置，比如`git branch -f master HEAD~3`意思是让master移动到HEAD的前3个位置，再比如，`git branch -f master c6`是让master直接移动到c6位置</span>

![027.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geuirwdlcoj30bw0b23yj.jpg)

```
git branch -f master HEAD~3
```

![028.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geuitex5l2j30bv0b3glo.jpg)

相对引用为我们提供了一种简洁的引用提交记录 `C1` 的方式， 而 `-f` 则容许我们将分支强制移动到那个位置。

## 通关记录

移动 `HEAD`，`master` 和 `bugFix` 到目标所示的位置。

目的：

![029.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geuiyavug8j30dw0jsglz.jpg)

开始：

![030.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geuj0sq4lnj308x0englv.jpg)

解法一：

```diff
git branch -f master C6
+git branch -f bugFix HEAD~2//这里移动bugFix分支到ＨＥＡＤ的前２位
git checkout C1
```

解法二：

```diff
git branch -f master c6
+git branch -f bugFix c0//这里直接移动bugFix分支到C0位置
git checkout c1
```

解法二出处：

<a href="https://www.jianshu.com/p/6e94b5592c40" class="LinkCard">Learn Git Branching 总结</a>

# 撤销变更

在 Git 里撤销变更的方法很多。和提交一样，撤销变更由底层部分（暂存区的独立文件或者片段）和上层部分（变更到底是通过哪种方式被撤销的）组成。我们这个应用主要关注的是后者。

主要有两种方法用来撤销变更 —— 一是 `git reset`，还有就是 `git revert`。接下来咱们逐个进行讲解。

## Git Reset

`git reset` 通过把分支记录回退几个提交记录来实现撤销改动。你可以将这想象成“改写历史”。`git reset` 向上移动分支，原来指向的提交记录就跟从来没有提交过一样。

> reset:重启

让我们来看看演示：

![031.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geulekpwt0j30bv0b3t8n.jpg)

```
git reset HEAD~1
```

![032.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geulje2d38j30bx0b2wef.jpg)

漂亮! Git 把 master 分支移回到 `C1`；现在我们的本地代码库根本就不知道有 `C2` 这个提交了。

（译者注：在reset后， `C2` 所做的变更还在，但是处于未加入暂存区状态。）

## Git Revert

虽然在你的本地分支中使用 `git reset` 很方便，但是这种“改写历史”的方法对大家一起使用的远程分支是无效的哦！

> revert:还原

为了撤销更改并**分享**给别人，我们需要使用 `git revert`。来看演示：

![033.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geulmmx7fcj30bv0b2t8n.jpg)

```
git revert HEAD 
```

![034.png](http://ww1.sinaimg.cn/large/006b3a9lgy1geulqk0onaj30bv0b23yh.jpg)

>奇怪！在我们要撤销的提交记录后面居然多了一个新提交！这是因为新提交记录 `C2'` 引入了**更改** —— 这些更改刚好是用来撤销 `C2` 这个提交的。也就是说 `C2'` 的状态与 `C1` 是相同的。
>
>revert 之后就可以把你的更改推送到远程仓库与别人分享啦。
>
><span style="background-color:yellow">原话过于羞耻以至于我不能放在正文里</span>

 

## 通关记录

要完成此关，分别撤销 `local` 分支和 `pushed` 分支上的最近一次提交。共需要撤销两个提交（每个分支一个）。

记住 `pushed` 是远程分支，`local` 是本地分支 —— 这么说你应该知道用分别哪种方法了吧？

```diff
-git reset HEAD~1
+git reset HEAD^
git checkout pushed
git revert HEAD
```

