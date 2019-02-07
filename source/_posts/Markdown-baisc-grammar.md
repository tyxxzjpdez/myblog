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

### 引用
#### 单层引用
**形式：**
`> something...`
**语法说明：**
引用需要在被引用的文本前加上>符号
**代码：**
``` md
> 这是一个有两段文字的引用
> 无意义的占行文字1.
> 无意义的占行文字2.
>
> 无意义的占行文字3.
> 无意义的占行文字4.
```
**显示效果：**
{%note default no-icon%}
> 这是一个有两段文字的引用
> 无意义的占行文字1.
> 无意义的占行文字2.
>
> 无意义的占行文字3.
> 无意义的占行文字4.
{%endnote%}
#### 多层引用（引用的嵌套）
**形式：**
`> something1...`
`>> something2...`
`>>> something3...`
**语法说明：**
区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的`>`
**代码：**
``` md
> 请问 Markdwon 怎么用？ - 小白
>> 自己看教程！ - 愤青
>>> 教程在哪？ - 小白
```
**显示效果：**
{%note default no-icon%}
> 请问 Markdwon 怎么用？ - 小白
>> 自己看教程！ - 愤青
>>> 教程在哪？ - 小白
{%endnote%}

### 插入图片
图片的创建方式与超链接相似，而且和超链接一样也有两种写法，**行内式**和**参考式**写法。
**语法说明：**语法中图片`Alt`的意思是如果图片因为某些原因不能显示，就用定义的图片`Alt`文字来代替图片。 图片`Title`则和链接中的`Title`一样，表示鼠标悬停与图片上时出现的文字。`Alt`和`Title`都不是必须的，可以省略，但建议写上。
#### 行内式
**形式：**
`![图片Alt](图片地址 "图片Title")`
**代码：**
``` md
![美丽花儿](http://ww2.sinaimg.cn/large/56d258bdjw1eugeubg8ujj21kw16odn6.jpg "美丽花儿")
```
**显示效果：**
{%note default no-icon%}
![美丽花儿](http://ww2.sinaimg.cn/large/56d258bdjw1eugeubg8ujj21kw16odn6.jpg "美丽花儿")
{%endnote%}
#### 参考式
**形式：**
`![图片Alt][标记]`(在文档要插入图片的地方)
`[标记]:图片地址 “Title”`(在文档后面其他位置)
**代码：**
``` md
![美丽花儿][flower]
[flower]:http://ww2.sinaimg.cn/large/56d258bdjw1eugeubg8ujj21kw16odn6.jpg  "美丽花儿"
```
**显示效果：**
{%note default no-icon%}
![美丽花儿][flower]
[flower]:http://ww2.sinaimg.cn/large/56d258bdjw1eugeubg8ujj21kw16odn6.jpg  "美丽花儿"
{%endnote%}

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

### 注脚
**形式：**
`脚注名字[^注脚名字]`
**语法说明：**
在需要添加注脚的文字后加上以上代码,称为加注。 然后在文本的任意位置(一般在最后)添加脚注，脚注前必须有对应的脚注名字。
**代码：**
```md
使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Leanote[^Le] 编辑器进行书写。
[^1]: Markdown是一种纯文本标记语言
[^2]: HyperText Markup Language 超文本标记语言
[^Le]: 开源笔记平台，支持Markdown和笔记直接发为博文
```
**显示效果：**
{%note default no-icon%}
使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2], 你可以使用 Leanote[^Le] 编辑器进行书写。
[^1]: Markdown是一种纯文本标记语言
[^2]: HyperText Markup Language 超文本标记语言
[^Le]: 开源笔记平台，支持Markdown和笔记直接发为博文
{%endnote%}

### 表格
**形式：**
形式较复杂，详细看下方的语法说明以及代码与效果
**语法说明：**
- 不管是哪种方式，第一行为表头，第二行分隔表头和主体部分，第三行开始每一行为一个表格行。
- 列与列之间用管道符|隔开。原生方式的表格每一行的两边也要有管道符。
- 第二行还可以为不同的列指定对齐方向。默认为左对齐，在-右边加上:就右对齐。

**代码1：**
```md
简单方式写表格：

学号|姓名|分数
-|-|-
小明|男|75
小红|女|79
小陆|男|92
```
**显示效果1：**
{%note default no-icon%}
简单方式写表格：

学号|姓名|分数
-|-|-
小明|男|75
小红|女|79
小陆|男|92
{%endnote%}
**代码2：**
```md
原生方式写表格：

| 学号 | 姓名 | 分数 |
| ---- | ---- | ---- |
| 小明 | 男   | 75   |
| 小红 | 女   | 79   |
| 小陆 | 男   | 92   |
```
**显示效果2：**
{%note default no-icon%}
原生方式写表格：

| 学号 | 姓名 | 分数 |
| ---- | ---- | ---- |
| 小明 | 男   | 75   |
| 小红 | 女   | 79   |
| 小陆 | 男   | 92   |
{%endnote%}
**代码3：**
```md
为表格第二列指定方向：

| 产品             |     价格 |
| ---------------- | -------: |
| Leanote 高级账号 |  60元/年 |
| Leanote 超级账号 | 120元/年 |
```
**显示效果3：**
{%note default no-icon%}
为表格第二列指定方向：

| 产品             |     价格 |
| ---------------- | -------: |
| Leanote 高级账号 |  60元/年 |
| Leanote 超级账号 | 120元/年 |
{%endnote%}

### LaTeX 公式
注意：需要在Font Matter加入`mathjax: true`
#### $ 表示行内公式
**代码：**
```md
质能守恒方程可以用一个很简洁的方程式 $E=mc^2$ 来表达。
```
**显示效果：**
{%note default no-icon%}
质能守恒方程可以用一个很简洁的方程式 $E=mc^2$ 来表达。
{%endnote%}
#### $$ 表示整行公式
**代码：**
```md
$$\sum_{i=1}^n a_i=0$$
$$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$
$$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$
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
```
**显示效果：**
{%note default no-icon%}
$$\sum_{i=1}^n a_i=0$$
$$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$
$$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$
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
{%endnote%}

访问[MathJax](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)参考更多使用方法。

### 分割线
**语法说明：**
你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：
**代码：**
```md
一些东西
***
另外一些东西
```
**显示效果：**
{%note default no-icon%}
一些东西
***
另外一些东西
{%endnote%}
虽然说在标准的语法中有好多分割线表示方法，但强烈推荐只使用一种作为习惯。

### 代码
插入程序代码的方式有两种，一种是利用缩进(Tab), 另一种是利用”`”符号（一般在ESC键下方）包裹代码。
**语法说明：**
- 插入行内代码，即插入一个单词或者一句代码的情况，使用\`code\`这样的形式插入。
- 插入多行代码，可以使用缩进或者\`code\`,具体看示例。
- 注意缩进式插入前方必须有空行

#### 行内式
**代码：**
```md
C语言里的函数`scanf()`怎么使用？
```
**显示效果：**
{%note default no-icon%}
C语言里的函数`scanf()`怎么使用？
{%endnote%}

#### 缩进式
在有些编辑器(比如默认设置的vscode)当中一般都用soft tab实现tab，这是由若干（看编辑器的配置）space组成的，并不是真的tab，所以很多时候你会发现按了tab键，代码却没有在markdown中变成代码块（详细资料见[这里](https://www.jianshu.com/p/9b76caae30f5)）
**代码：**
```c
  #include <stdio.h>
  int main(void)
  {
      printf("Hello world\n");
  }
```
**显示效果：**

	#include<stdio.h>
	int main(){
		printf("123");
		return 0;
	}

#### 用三个”`”包裹多行代码
注意：此处在代码中出现了反引号，解决方案在[这里](https://www.jianshu.com/p/d6ca2d4dfaab)，简单来说就是外层反引号由三个变成四个
**代码：**
````md
```c
#include <stdio.h>
int main(void)
{
  printf("Hello world\n");
}
```
````
**显示效果：**
```c
#include <stdio.h>
int main(void)
{
  printf("Hello world\n");
}
```

### 流程图
Markdown语法是支持流程图、序列图的。但是我们需要安装一个插件来实现。
插件地址：<https://github.com/bubkoo/hexo-filter-flowchart>
#### 安装
先进入你的博客根目录，然后输入以下命令
```bash
npm install --save hexo-filter-flowchart
```
#### 使用
打开你的hexo博客的**站点配置文件**_config.yml 。
然后找一个位置，把下面的代码复制进去，注意对齐和缩进。这是为了方便自定义该插件的配置选项，我们只需要修改以下少量代码就可成功配置，而不必去烦乱的代码里修改插件的配置文件。(当然即使你不去博客的配置文件中进行配置，也是可以正常使用的。如果你不会添加，请忽略此步)
```yml
flowchart:
  # raphael:   # optional, the source url of raphael.js
  # flowchart: # optional, the source url of flowchart.js
  options: # options used for `drawSVG`
```
我们可以根据自己的使用习惯进行修改，默认配置为如下所示。我们同时需要根据该默认配置来自定义配置。
```yml
{
  "raphael": "https://cdnjs.cloudflare.com/ajax/libs/raphael/2.2.7/raphael.min.js",
  "flowchart": "https://cdnjs.cloudflare.com/ajax/libs/flowchart/1.6.5/flowchart.min.js",
  "options": {
    "scale": 1,
    "line-width": 2,
    "line-length": 50,
    "text-margin": 10,
    "font-size": 12
  }
}
```
#### 测试
接下来我们可以用markdown语法画一个流程图来测试一下是否已经安装成功。[语法参照](http://flowchart.js.org/)
**代码：**
下方代码flow前的\需要**去掉**，我是因为实在不知道怎么取消转为`div`块，所以不得已加了一个反斜杠
````
```\flow
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes
or No?|approved:>http://www.google.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|request

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
```
````
**显示效果：**
{%note default no-icon%}
```flow
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine|invalid
cond=>condition: Yes
or No?|approved:>http://www.google.com
c2=>condition: Good idea|rejected
io=>inputoutput: catch something...|request

st->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
```
{%endnote%}

### 特殊字符转义
#### 反斜杠
该部分转载于[这里](https://www.appinn.com/markdown/)
Markdown 可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果（但不用`<em>`标签），你可以在星号的前面加上反斜杠：
```md
\*literal asterisks\*
```
Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
```md
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
```
#### html转义字符
点击[这里](http://tool.oschina.net/commons?type=2)查看全部
以下是部分常用的转义字符：

| 字符 | 十进制 | 转义字符 |
| ---- | ---- | ---- |
| " | &amp;#34;   | &amp;quot; |
| ' | &amp;#39;   | &amp;apos; |
| & | &amp;#38;   | &amp;amp;   |
| < | &amp;#60;   | &amp;lt;   |
| > | &amp;#62;   | &amp;gt;   |
| 不断开空格(non-breaking space) | &amp;#160;   | &amp;nbsp;   |

##参考
[LixT's Blog](https://www.lixint.me/markdown.html)
[ThitjerShore's Blog](https://blog.csdn.net/thither_shore/article/details/52181464)
[bingyu's blog](https://www.bingyublog.com/2018/08/22/Hexo%E5%8D%9A%E5%AE%A2%E6%98%BE%E7%A4%BAmarkdown%E6%B5%81%E7%A8%8B%E5%9B%BE/)
