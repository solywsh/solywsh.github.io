---
title: python笔记part1
date: 2020-04-07 18:26:00
catalog: true
tags: [python]
categories: python
---

<meta name="referrer" content="no-referrer"/>

我最近也开始看python相关的书籍了，老实说如果计算机语言有母语的话，python无疑是我接触最早的语言了——也是荒废最早的。那时候大部分人还是用的python2，还没见过易语言这种神奇的‘语言’。

看到字典相关内容的时候，我测试了一下代码：

```python
alien_0 = {'color':'green','points':5}
alien_0['site'] = 1234 
for k,v in alien_0.items():
    print("the key:"+k+"\nthe value:"+str(v)+"\n")
```

输出结果是：

```
the key:color
the value:green

the key:points
the value:5

the key:site
the value:1234
```

让我感到兴趣的是，` print("the key:"+k+"\nthe value:"+str(v)+"\n")`这里的加号也可以换成`,`号，当然意思完全不一样。书中并没有做详细的说明，于是我便开始研究起来。

这里推荐一个很好用的轻量级的python编辑器`Thonny`，很适合初学者，我最近折腾`microbit`也是用的这个，甚至可以将错误提示替换成中文，如果需要的话可以在底下评论区留言，我会出一篇简单的教程。

回到`print`，我这里将`print("the key:"+k+"\nthe value:"+str(v)+"\n")`的`str(v)`替换成`v`，有趣事情发成了，当我按下F5时，shell提示我：

```python
Python给的消息：
        TypeError: can only concatenate str (not "int") to str
        
    TypeError这个错误通常是你把两个不同类型的对象放在一起运算了。
    或者函数调用的参数给错类型，
    或者把对象类型搞错了，做了一个其它类型才能做的操作。
    
    从Python给的信息来看，可能是如下的原因：
        你想把两个不同类型的对象加（+）起来：
        1个字符串（“str”） 和 1个整数（“int”）
        不同类型的对象不能简单就相加
        
    在源文件’F:\StudyDate\python\code\tset\tset.py’的第4行执行中止了。
    错误就在这行代码或者附近！
    
       2: alien_0['site'] = 1234
       3: for k,v in alien_0.items():
    -->4:     print("the key:"+k+"\nthe value:"+v+"\n")

    k: 'points'
    v: 5
```

原因其实很简单，就是我添加了一个键-值对`alien_0['site'] = 1234` 时，1234不是'1234',也就是说，1234是`int`整数类型而不是`str()`字符类型，在相加时，只能同类型相加，你总不能要求他处理“二”+1等于几吧。

将`v`两边的`+`替换成` , 

```python
print("the key:"+k+"\nthe value:",v,"\n")
```

输出结果为：

```
the key:color
the value: green 

the key:points
the value: 5 

the key:site
the value: 1234
```

可以注意到的是，在`the value:`后面的所跟的值都空了两个，这里大概的意思是参数或者变量间的分隔(链接符)，python在处理时会自动为`,`的两边参数或者变量打上两个空格。在python2的时候甚至可以用它来避免输出时自动换行的情况。

![Image](https://i0.hdslb.com/bfs/album/43cacb9b301f4f4c23a68a7dcfa1982f74b52528.jpg)