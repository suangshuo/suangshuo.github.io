---
layout : post
title : "ncurses库使用教程"
date: 不定期更改 
tags: [everyday]
comments: true
author: suangshuo
---

# ncurses库使用教程
众所周知,ncurses库非常好用,像vim和nvim都是ncurses实现的.它还可以做小游戏,<br>
这篇文章末尾会贴上一些小作品,让我们一起看一看ncurses库能做什么吧!
## 介绍
> 本段内容引用自(这篇文章)[https://zhuanlan.zhihu.com/p/33640653]
ncurses(new curses)是一套编程库，它提供了一系列的函数以便使用者调用它们去生成基于文本的用户界面<br>
ncurses名字中的n意味着“new”，因为它是curses的自由软件版本。由于AT&T“臭名昭著”的版权政策，人们不得不在后来用ncurses去代替它<br>
ncurses是GNU计划的一部分，但它却是少数几个不使用GNU GPL或LGPL授权的GNU软件之一<br>

其实我们对ncurses本身并不陌生，以下几款大名鼎鼎的软件都用到过ncurses：
- vim
- emacs
- lynx
- screen
## 安装
homebrew:
~~~ sh
brew install ncurses
~~~
apt:
~~~ sh
sudo apt install libncurses5
~~~
pacman:
~~~ sh
pacman -S ncurses ncurses-devel
~~~
yum:
~~~ sh
yum install ncurses ncurses-devel
~~~
