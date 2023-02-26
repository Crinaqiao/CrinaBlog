---
title: >-
  Git报错:remote: Support for password authentication was removed on August
  13,.(删除了对密码身份验证的支持。)
tags:
  - Git
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=11872
feature: false
date: 2022-09-13 23:48:15
---
# 一、报错
> remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.

> remote：2021 年 8 月 13 日删除了对密码身份验证的支持。
远程：有关当前推荐的身份验证模式的信息，请参阅 https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls。

# 二、解决办法
**去生成一个token，使用token验证推送**
> https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token