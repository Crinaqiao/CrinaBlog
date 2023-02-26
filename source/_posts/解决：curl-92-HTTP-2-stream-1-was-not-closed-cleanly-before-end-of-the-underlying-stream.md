---
title: >-
  解决：curl: (92) HTTP/2 stream 1 was not closed cleanly before end of the
  underlying stream
tags:
  - Git
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=183247
feature: false
date: 2022-11-01 12:13:35
---
# 提示默认通信协议出错
```bash
curl: (92) HTTP/2 stream 1 was not closed cleanly before end of the underlying stream
```
## 解决办法：更改默认通信协议
```bash
git config --global http.version HTTP/1.1
```
## 重启终端，再次运行命令