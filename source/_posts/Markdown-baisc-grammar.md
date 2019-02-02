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

### 斜体,粗体和高亮
代码：
```
*斜体*
**粗体**
***加粗斜体***
~~删除线~~
<mark>高亮</mark>
```
显示结果：
{% note default no-icon%}
*这是一段斜体*
**这是一段粗体**
***这是一段加粗斜体***
~~这是一段删除线~~
<mark>这是一段高亮</mark>
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
`[链接文字](链接地址 "链接标题")`
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
`[链接文字][链接标记]`
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

#### 自动链接
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

#### 锚点
网页中，锚点其实就是页内超链接，也就是链接本文档内部的某些元素，实现当前页面中的跳转。比如我这里写下一个锚点，点击回到目录，就能跳转到目录。 在目录中点击这一节，就能跳过来。还有下一节的注脚。这些根本上都是用锚点来实现的。**注意：Markdown 只支持在标题后插入锚点，其它地方无效。**
**形式：**
`{% raw %}### 目录{#index}{% endraw %}`
`跳转到[目录](#index)`
**语法说明：**
{%raw%}在你准备跳转到的指定标题后插入锚点{#标记}，然后在文档的其它地方写上连接到锚点的链接。{%endraw%}**{%raw%}注意此项不能直接在Hexo博客中使用，Hexo博客会将{}中的内容进行渲染，从而引起未知错误(此时可使用{%raw%}{%endraw%}取消渲染)。{%endraw%}**
**代码：**
```
跳转到[超链接](#超链接)
```
**显示效果：**
{%note default no-icon%}
跳转到[超链接](#超链接)
{% endnote %}

### 列表
#### 无序列表
使用`*,+,-`来表示无序列表。
**代码：**
```
- 无序列表项 一
- 无序列表项 二
- 无序列表项 三
```
**显示效果：**
{%note default no-icon%}
- 无序列表项 一
- 无序列表项 二
- 无序列表项 三
{%endnote%}
#### 有序列表
有序列表则使用数字接着一个英文句点。
**代码：**
```
1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三
```
**显示效果：**
{%note default no-icon%}
1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三
{%endnote%}
#### 定义型列表
**形式：**
`sth`
`:+Tab`
**语法说明：**
定义型列表由名词和解释组成。一行写上定义，紧跟一行写上解释。解释的写法:紧跟一个缩进(Tab)
**代码：**
```
Markdown
:    轻量级文本标记语言，可以转换成html，pdf等格式（左侧有一个可见的冒号和四个不可见的空格）

代码块 2
:    这是代码块的定义（左侧有一个可见的冒号和四个不可见的空格）
        代码块（左侧有八个不可见的空格）
```
**显示效果：**
经过试验，在hexo下并不支持定义型列表，所以此处只能贴一张效果图：
![效果图](/myblog/images/Local-Gallery/markdown-definitionList.png "定义型列表")

### 字体颜色与字体背景颜色
大致的策略是字体颜色使用font标签(**可内联**)，背景色使用一行一列的表格进行填充（**不可内联**）
**更新：现在可以使用&lt;span&gt;标签加上style的声明同时实现前景与背景颜色的修改**
一般**不建议**改颜色，不过若实在有需要，可以点[这里](http://www.w3school.com.cn/tags/html_ref_colornames.asp)查看更多颜色来搭配
**代码：**
```
<font face="STCAIYUN" color=#0099ff size=3 >我是华文彩云</font>
你能变色吗？<span style="color:blue;background-color:rgb(255,204,204)">哈哈，我能变色啦！</span>
<table><tr><td bgcolor=PowderBlue>这里的背景色是：PowderBlue，  十六进制颜色值： #B0E0E6，rgb(176, 224, 230)</td></tr></table>
```
**显示效果：**
{% note default no-icon %}
<font face="STCAIYUN" color=#0099ff size=3 >我是华文彩云</font>
你能变色吗？<span style="color:blue;background-color:rgb(255,204,204)">哈哈，我能变色啦！</span>
<table><tr><td bgcolor=PowderBlue>这里的背景色是：PowderBlue，  十六进制颜色值： #B0E0E6，rgb(176, 224, 230)</td></tr></table>
{% endnote %}

### 特殊字符转义

##参考
[LixT's Blog](https://www.lixint.me/markdown.html)
[ThitjerShore's Blog](https://blog.csdn.net/thither_shore/article/details/52181464)
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
