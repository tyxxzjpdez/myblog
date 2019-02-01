---
title: Markdown基本语法
date: 2019-01-29 22:40:30
sticky: 0
mathjax: true
tags:
  - Markdown
categories:
  - 博文书写规范
photos: 
  - /images/Local-Gallery/markdown.jpg
---

{% cq %}
    第一篇正式博客，因为对Markdown语法不熟悉，就打算专门写个关于Markdown语法的博客
    **注意：本博客仅仅是总结其他博客的用法，末尾会给出所有的链接**
{% endcq %}

<!-- more -->

## 快速开始

### 斜体和粗体

代码：
```
*斜体*
**粗体**
***加粗斜体***
~~删除线~~
```
显示结果：
{% note default no-icon%}
*这是一段斜体*
**这是一段粗体**
***这是一段加粗斜体***
~~这是一段删除线~~
{% endnote %}

### 分级标题

写法：
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
### 超链接

Markdown 支持两种形式的链接语法： 行内式和参考式两种形式，行内式一般使用较多。
#### 行内式
**形式：**
\[链接文字\]\(链接地址 "链接标题"\)
**语法说明：**
[]里写链接文字，()里写链接地址, ()中的”“中可以为链接指定title属性，title属性可加可不加。title属性的效果是鼠标悬停在链接上会出现指定的title文字，链接地址与链接标题前有一个空格。
**代码：**
```
欢迎来到[我的博客](https://tyxxzjpdez.github.io/myblog)
欢迎来到[我的博客](https://tyxxzjpdez.github.io/myblog "tyxxzjodez's Blog")
```
**显示效果：**
{% note default no-icon%}
欢迎来到[我的博客](https://tyxxzjpdez.github.io/myblog)
欢迎来到[我的博客](https://tyxxzjpdez.github.io/myblog "tyxxzjodez's Blog")
{% endnote %}

#### 参考式
参考式超链接一般用在学术论文上面，或者另一种情况，如果某一个链接在文章中多处使用，那么使用引用 的方式创建链接将非常好，它可以让你对链接进行统一的管理。
**形式：**
\[链接文字\]\[链接标记\]
**语法说明：**
参考式链接分为两部分：链接文字与链接标记。
对于链接标记，在文本的任意位置添加\[链接标记\]:链接地址 “链接标题”，注意链接地址与链接标题前有一个空格。
对于链接文字，就是显示的文字，而如果链接文字本身可以做为链接标记，你也可以写成\[链接文字\]\[\]，而相应的链接标记可以变成\[链接文字\]：链接地址的形式，见代码的最后一行。
**代码：**
```
我经常去的几个网站[Google][1]、[Leanote][2]以及[自己的博客][3]
[Leanote 笔记][2]是一个不错的[网站][]。
[1]:http://www.google.com "Google"
[2]:http://www.leanote.com "Leanote"
[3]:https://tyxxzjpdez.github.io/myblog "tyxxzjpdez's Blog"
[网站]:http://http://blog.leanote.com
```
**显示效果：**
{% note default no-icon %}
我经常去的几个网站[Google][1]、[Leanote][2]以及[自己的博客][3]
[Leanote 笔记][2]是一个不错的[网站][]。
[1]:http://www.google.com "Google"
[2]:http://www.leanote.com "Leanote"
[3]:https://tyxxzjpdez.github.io/myblog "tyxxzjpdez's Blog"
[网站]:http://http://blog.leanote.com
{% endnote %}

### 自动链接

Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用<>包起来， Markdown 就会自动把它转成链接。一般网址的链接文字就和链接地址一样。
**代码：**
```
<https://tyxxzjpdez.github.io/myblog/>
<address@example.com>
```
**显示效果：**
{% note default no-icon%}
<https://tyxxzjpdez.github.io/myblog/>
<address@example.com>
{% endnote %}

##参考
[LixT's Blog](https://www.lixint.me/markdown.html)
{% note default no-icon %}
    $$\begin{bmatrix}
        {a_{11}}&{a_{12}}&{\cdots}&{a_{1n}}\\
        {a_{21}}&{a_{22}}&{\cdots}&{a_{2n}}\\
        {\vdots}&{\vdots}&{\ddots}&{\vdots}\\
        {a_{m1}}&{a_{m2}}&{\cdots}&{a_{mn}}\\
    \end{bmatrix}$$
    $$\begin{array}{c|lll}
    {↓}&{a}&{b}&{c}\\
    \hline
    {R_1}&{c}&{b}&{a}\\
    {R_2}&{b}&{c}&{c}\\
    \end{array}$$
{% endnote %}
