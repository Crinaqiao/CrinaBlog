---
title: Rust文件分层
tags:
  - Rust
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=18728374
feature: false
date: 2022-09-15 21:09:26
---
>使用 mod my 引入文件，
rust会自动去寻找my.rs或者my/mod.rs。
找到该文件后会将文件内容放到此作用域
一个名为·my·的模块里面

### main.rs
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/%E6%88%AA%E5%9B%BE_%E9%80%89%E6%8B%A9%E5%8C%BA%E5%9F%9F_20220915210841.png)
### my/mod.rs
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/%E6%88%AA%E5%9B%BE_%E9%80%89%E6%8B%A9%E5%8C%BA%E5%9F%9F_20220915212118.png)
