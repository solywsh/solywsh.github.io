---
title: Hello World
catalog: true
date: 2020-03-05 16:26:42
tags: test
categories: hello
---
Welcome ！请记住这个[网站](http://solywsh.github.io)

<a href="http://violetwsh.com" class="LinkCard">我的的个人博客</a>

我在腾讯云那儿买了一个域名，因为我是我新用户，在一定时间类暂时不能在注册局备案，所以blog的域名现在还换不了，但是也请记住！www.voiletwsh.com 不久就会换的。

<!--more-->

## 关于这个blog

### 这个blog的产生

在这个想法产生的时候，我还在老师的课堂中昏昏欲睡，然后不知不觉的就做出来了。不过中间踩了很多坑就是了，磕磕绊绊地，拖欠了一大堆作业，才有如今这简陋的样子。

### blog的未来使用

最初的目的只是将自己学计算机时的一些笔记发布上来，起到监督自己的作用。按照自己鸽子的特性（人类的本质），也许没过多久就不更了吧。甚至被删也是可能的——在建这个blog的时候就被我删了4次。

后来发现blog还有些其他用处，比如自己的相册，加密之后也可以写日记之类的。

当然，也可以到我的github这里玩玩吧: [github-solywsh](https://github.com/solywsh/)

### 最近

最近比较忙，blog的内容暂时是程序设计的作业吧。

### 以下为测试内容

以后的计算机内容可能以c为主，当然我也想多学习一些python和linux。

``` c
#include <stdio.h>

int main(void)
{
	double a,b,c,x,S;
	scanf("%lf %lf %lf", &a, &b, &c);
	x = (a + b + c) / 2;
	S = sqrt(x * (x - a) * (x - b) * (x - c));
	if (a + b < c)
		printf("不能构成三角形\n");
	else
	{
		if (a + c < b)
			printf("不能构成三角形\n");
		else
		{
			if (b + c < a)
				printf("不能构成三角形\n");
			else
			{
				printf("%.3lf", S);
			}
		}
	}
	return 0;
}

/*在最后if条件可以这样改：

if (a + b > c && a + c > b && b + c > a)
		printf("不能构成三角形\n");
	else
	{
		printf("%.3lf", S);
	}

*/
```


