---
title: zsh的安装与相关配置
sticky: 0
mathjax: true
date: 2019-02-04 13:59:09
tags:
  - zsh
categories:
  - Linux
photos:
  - /images/Local-Gallery/oh-my-zsh.png
---
> 昨天实在是嫌shell找东西老实要不停cd，ls太麻烦,就去网上找找有没有什么高效的办法，结果一查，没想到我用的zsh只要配置一下插件就可以。然后趁着这功夫，我特意找了找zsh上的其他有用插件，结果时间花了不少，但收获也不少。

<!-- more -->

# 安装

## 安装zsh

``` bash
sudo apt install zsh
```

## 将默认shell改为zsh

``` bash
chsh -s /bin/zsh
```

> 注意：不要sudo,用当前用户的权限即可

## 安装git

``` bash
sudo apt install git
```

## 安装oh-my-zsh

``` bash
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

# 配置（重点）

**注意：**其实有了oh-my-zsh之后，配置插件就变得很系统化，一般都是如下步骤：

1. 先查看`~/.oh-my-zsh/plugins`中有没有自己想要的插件，**有则转2，无则转3**。
2. 直接查看具体的插件目录下的\*.plugin.zsh，看是否有自己需要额外安装的命令，若有则安装一下。**下转4**
3. 若是在github上（这个条件基本都满足），直接使用命令`git clone https://github.com/*.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/*`，否则可以查找相关资料，去官网或者`sudo apt install *`之类的。**下转4**
4. 将插件名加入到`~/.zshrc`里的`plugins`变量中（有些插件有位置的要求，要注意一下）。**结束**

而所有插件的用法一般都有以下方式方式获取：

1. 对于在`~/.oh-my-zsh/plugins`有的插件，直接查看`README.md`即可
2. 去官网寻找docs或者去相关github主页找READ.md文件查看
3. 直接`cmd --help`或者`man cmd`(cmd指代插件指令)
4. 查看源代码
5. 实在没有地方查看用法，或者图省事，可直接baidu或google

## git

> 该插件在安装完oh-my-zsh是自动已经配置好的，主要是提供了有关git的一些`alias`和`function`。

## wd

> `wd`的作用就是能够快速的切换到常用的目录。我们用命令行时经常会遇到这样一种情况，我们常用的目录就那么几个，而这些目录有时候会再很深的层级中。使用`cd`命令在这些深层级目录中切换就比较耗费时间了。

配置办法：
由于oh-my-zsh已经内置了该插件，直接在`~/.zshrc`中的`plugins`加入`wd`这一项就好

## thefuck

> The Fuck is a magnificent app, inspired by a [@liamosaur](https://twitter.com/liamosaur/) [tweet](https://twitter.com/liamosaur/status/506975850596536320),that corrects errors in previous console commands.

配置方法(On Ubuntu / Mint)：

``` bash
sudo apt update
sudo apt install python3-dev python3-pip python3-setuptools
sudo pip3 install thefuck
```

然后在`~/.zshrc`中的`plugins`加入`thefuck`这一项就好

## zsh-autosuggestions

> 超级好用！强力推荐
> It suggests commands as you type, based on command history.

配置方法：
`git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions`
然后在`~/.zshrc`中的`plugins`加入`zsh-autosuggestions`这一项就好

## zsh-syntax-highlighting

> This package provides syntax highlighting for the shell zsh. It enables highlighting of commands whilst they are typed at a zsh prompt into an interactive terminal. This helps in reviewing commands before running them, particularly in catching syntax errors.

配置方法：
`git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting`
然后在`~/.zshrc`中的`plugins`加入`zsh-syntax-highlighting`这一项就好(为识别所有命令，尽量加在所有plugins的最后)

## history-substring-search

> This is a clean-room implementation of the Fish shell's history search feature, where you can type in any part of any command from history and then press chosen keys, such as the UP and DOWN arrows, to cycle through matches.

配置方法：
由于oh-my-zsh已经内置了该插件，直接在`~/.zshrc`中的`plugins`加入`history-substring-search`这一项就好

## autojump

> autojump is a faster way to navigate your filesystem. It works by maintaining a database of the directories you use the most from the command line.

配置方法：
具体配置方法，可以去[官网](https://github.com/wting/autojump)，这里只说明我自己做过的配置方法，我是使用手动git代码仓库安装的：

``` bash
git clone git://github.com/wting/autojump.git
cd autojump
./install.py`
```

然后系统提示将如下代码放在`~/.zshrc`中

``` bash
[[ -s /home/tyxxzjpdez/.autojump/etc/profile.d/autojump.sh ]] && source /home/tyxxzjpdez/.autojump/etc/profile.d/autojump.sh
autoload -U compinit && compinit -u
```

第一句代码的意思很显然，对于第二句代码，经过翻看[参考](http://zsh.sourceforge.net/Doc/Release/Completion-System.html#Use-of-compinit),还有部分源码以及`~/.oh-my-zsh/oh-my-zsh.sh`中代码，我认为第一句必需，第二句可以省略。

# 参考

[Dom_留声机's Blog](https://blog.csdn.net/qq_14824885/article/details/81098091)
[askDing's Blog](https://www.cnblogs.com/mitnick/p/6270384.html)
[github-thefuck](https://github.com/nvbn/thefuck)
[github-zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
[github-zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
[github-zsh-history-substring-search](https://github.com/zsh-users/zsh-history-substring-search)
[github-autojump](https://github.com/wting/autojump)