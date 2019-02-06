---
title: Linux系统中的剪贴板
sticky: 0
mathjax: true
date: 2019-02-06 16:51:36
tags:
  - clipboard
categories:
  - Linux
photos:
  - /images/Local-Gallery/clipboard.jpg
---
> 很久以前就对Linux下的剪贴板感到奇怪，前一段时间仔细查了相关资料，发现真的和windows下差距很大。

<!-- more -->

# 选择缓冲区和剪切板

不同于Windows，Linux系统里存在两种剪切板：一个叫做选择缓冲区(X11 selection buffer)，另一个才是剪切板(clipboard)。

## 选择缓冲区

选择缓冲区是实时的，当使用鼠标或键盘选择内容时，内容已经存在于选择缓冲区了，这或许就是选择缓冲区的由来吧。
使用下面的命令查看选择缓冲区的内容：

``` bash
xclip -out
```

如果没有xclip命令，Debian/Ubuntu下可以通过如下命令安装：

``` bash
sudo apt-get install xclip
```

可以使用鼠标中键或键入**Shift+Insert**来粘贴选择缓冲区的内容。但对于有些GUI程序，比如gedit和firefox browser，只能通过鼠标中键调用选择缓冲区的内容，使用**Shift+Insert**的话，调用的是剪切板的内容。

以上缓冲区都是指`primary selection`，但是通过`xclip`的帮助文档不难发现，还有一个`secondary selection`，就目前来说，该区域似乎只能通过`xclip`命令来使用，没有其他接口可以使用它。

## 剪切板

剪切板和Windows的剪切板类似，在选择文字内容后，执行**Ctrl + c**或在菜单里选择‘复制’的话，这时内容才存放到剪切板里。

使用下面的命令查看剪切板的内容：

``` bash
xclip -out -sel clipboard
```

而使用剪切板的内容，则是**Ctrl+v**。 但在有些情况下，比如gnome-terminal，不能直接使用**Ctrl+c**，**Ctrl+v**，这时就要用**Shift+Ctrl+c**，**Shift+Ctrl+v**代替。

# 参考

[原文](https://www.cnblogs.com/jianyungsun/archive/2011/03/19/1988855.html)
[clipboard wiki](https://wiki.archlinux.org/index.php/clipboard)