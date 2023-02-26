---
title: Linux使用screen让程序在后台运行
tags:
  - Linux
categories:
  - 运维
cover: https://picsum.photos/1080/1080?random=1349857
feature: false
date: 2022-10-27 16:50:43
---
# Linux使用screen让程序在后台运行

:::tip 介绍screen
screen 是一个非常有用的命令，提供从单个 SSH 会话中使用多个 shell 窗口（会话）的能力。当会话被分离或网络中断时，screen 会话中启动的进程仍将运行，你可以随时重新连接到 screen 会话。如果你想运行一个持久的进程或者从多个位置连接到 shell 会话，这也很方便。
:::

## 一、安装 screen
- CentOS/RedHat/Fedora
```bash
yum install screen
```
- Ubuntu/Debian
```bash
apt-get install screen
```


## 二、在后台运行程序
- 输入以下命令
> xxx 代表在后台运行的 screen 作业名称，可以随便给（建议取有意义的名字）
```bash
screen -S xxx
```

- 执行完上一条命令后终端会打开一个类似新窗口的页面（screen会话），我们再运行要在后台执行的程序
> `code-server`是我要在后台运行的程序，视你自己情况而定
```bash
code-server
```

## 三、从 screen 会话中分离
> 要从当前的 screen 会话中分离，你可以按下 `Ctrl-A` 和 `d`。所有的 screen 会话仍将是活跃的，你之后可以随时重新连接。

## 四、重新连接到 screen 会话
- 如果你从一个会话分离，或者由于某些原因你的连接被中断了，你可以使用下面的命令重新连接：
```bash
screen -r
```

- 如果你有多个 screen 会话，你可以用 ls 参数列出它们。
```bash
screen -ls
There are screens on:
7880.session    (Detached)
7934.session2   (Detached)
7907.session1   (Detached)
3 Sockets in /var/run/screen/S-root.
```

- 在我们的例子中，我们有三个活跃的 screen 会话。因此，如果你想要还原 “session2” 会话，你可以执行：
```bash
screen -r 7934
```
或者使用 screen 名称。
```bash
screen -r -S session2
```

## 五、中止 screen 会话
>有几种方法来中止 screen 会话。你可以按下 `Ctrl+d`，或者在命令行中使用 `exit` 命令。
要查看 screen 命令所有有用的功能，你可以查看 screen 的 `man` 手册。
```bash
man screen
NAME
screen - screen manager with VT100/ANSI terminal emulation
SYNOPSIS
screen [ -options ] [ cmd [ args ] ]
screen -r [[pid.]tty[.host]]
screen -r sessionowner/[[pid.]tty[.host]]
```