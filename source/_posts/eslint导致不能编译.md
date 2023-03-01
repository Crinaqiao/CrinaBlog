---
title: eslint与保存自动格式化冲突导致不能编译
tags:
  - eslint
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=12214
feature: false
date: 2022-08-16 17:51:01
---
**问题**
ctrl+s保存后，vue在estline的要求下，格式发生变化，导致不能完成编译，
所以取消保存时自动格式化。
**解决**
操作：在vs的应用商城中禁用jS-CSS-HTML Formatter