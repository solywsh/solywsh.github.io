---

title: C语言期末OJ考试
date: 2020-04-27 18:26:00
catalog: true
tags: [考试,C语言,程序设计,分享]
categories: homework

---

<meta name="referrer" content="no-referrer"/>

{% note danger %}
声明：

本文代码严禁复制分享以及用于考试，此博客内容仅为个人学习笔记！

{% endnote %}

# 回文字符串

**题目内容：**输入一个字符串，判断该字符串是否为回文，是则输出“true”，否则输出“false”。

回文是对称相同的字符串，比如“level”。

**编码建议:**在主函数中进行输出输出格式的处理。

定义函数 `int func(char *s)` 用来判断s所指向的字符串是否为回文。

**输入格式:**  字符串

**输出格式：**true/false

**输入样例：**level

**输出样例：**true

**感谢张元瑞提供的代码**

```c
#include<stdio.h>
#include<string.h>
int main(){
	int func(char *s);
	char a[20];
	int c;
	gets_s(a);//注意这里在某些编译器应该写作 gets_s(a,20);
	c = func(a);
	if (c == 1)printf("ture");//这里有错
	else printf("false");
	return 0;}//代码由张元瑞同学提供
int func(char *s){
	int i, n;
	n = strlen(s);
	for (i = 0; i <= n / 2; ++i){
		if (s[i] != s[n - i - 1])return 0;}
	return 1;}
```

做了一些适合自己习惯的修改

```c
#include<stdio.h>
#include<string.h>
int main(){
	void func(char* s);
	char a[20];
	gets(a);
	func(a);
	return 0;
}//violetwsh.com
void func(char* s){
	int i, n = strlen(s);
	for (i = 0; i <= n / 2; ++i)
	{
		if (s[i] != s[n - i - 1])
		{printf("false"); return;}
	}
	printf("ture"); return;
}
```

**以上都是错误答案**

**以上都是错误答案**

**以上都是错误答案**

**以上都是错误答案**

**以上都是错误答案**

**以上都是错误答案**

**以上都是错误答案**

**以上都是错误答案**

**正确答案**：（感谢刘莹雷勇士提供的代码，这里安慰一下他）

``` c
#include <stdio.h>
#include <string.h>
void func(char *p,int n);
int main()
{
	char vrb[100];
	int n;
	gets(vrb);
	n=strlen(vrb);
	func(vrb,n);
	return 0;
}//violetwsh.com
void func(char *p,int n) {
	int i,j;
	for(i=0,j=n-1;i<j;)
	if(*(p+i++)!=*(p+j--)) break;
	if(i>=j) printf("true");
	else printf("false");
}
```

为什么前面两个代码是错的呢？

我们只需要定义一下

```c
#define true ture
```

。。。。。。

希望大家写代码一定要长眼睛

![Image](https://i0.hdslb.com/bfs/album/18a2e4f5f46b5df0192fec6d61083401b4013ad6.png)

# 汽车行驶

**题目内容：**

根据汽车行驶的起点和终点坐标，计算汽车行驶距离和燃油消耗，有如下条件：

- 汽车行车路线为起点到终点的直线
- 汽车初始位置坐标为（3，0），燃油初始量为100升
- 汽车行驶油耗为8升/公里
- 输入为终点的横纵坐标，输出为到达终点的剩余油耗（不能到达则输出0.00，保留两位小数）

**编码建议:**

汽车数据结构如下，三个成员分别表示横坐标、纵坐标、剩余油耗

``` c
struct car {
    double x;
    double y;
    double fuel;
};
```

在主函数中进行输入输出的格式处理

定义 `double func(struct car start, struct car end)` 用来计算起点到终点的剩余油耗

**输入格式:**终点x坐标,终点y坐标

**输出格式：**剩余油耗或0.00

**输入样例：**4,1

**输出样例：**88.69

**输入样例：**100,100

**输出样例：**0.00

写的时候有点慌忙，所以就按照自己的习惯来了，一些题目规范的函数就没有使用

```c
#include<stdio.h>
#include<math.h>
#define OIL 100
#define use 8
typedef struct {
	double x;
	double y;
	double fuel;
}Car;
Car start = { 3,0,OIL };
int main()
{
	Car final;
	double count(Car place);
	scanf("%lf,%lf", &final.x, &final.y);
	final.fuel = count(final);
	if (final.fuel > 0)
		printf("%.2lf", final.fuel);
	else printf("0.00");
	return 0;
}//violetwsh.com
double count(Car place)
{
	double distance, x_1, y_1, last;
	x_1 = (start.x - place.x) * (start.x - place.x);
	y_1 = (start.y - place.y) * (start.y - place.y);
	distance = sqrt(x_1 + y_1);
	last = OIL - (distance * use);
	return (last);
}

```

![img](https://i0.hdslb.com/bfs/album/ce760f248c66684ebbb7d932fc5d53939adcb336.png@518w_1e_1c.png)