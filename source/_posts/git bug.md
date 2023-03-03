---
title: warning: in the working copy of ‘...‘, LF will be replaced by CRLF the next time Git touche
tags:
  - git
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=12218
feature: false
date: 2022-08-16 17:51:01
---

## 解决问题：
### 情况一：windows用户
`git config --global core.autocrlf true`
### 情况二：linux/mac用户
` git config --global core.autocrlf input`

### 情况三：Windows 程序员
```
#提交检出均不转换
git config --global core.autocrlf false
你也可以在文件提交时进行safecrlf检查
 
#拒绝提交包含混合换行符的文件
git config --global core.safecrlf true   
 
#允许提交包含混合换行符的文件
git config --global core.safecrlf false   
 
#提交包含混合换行符的文件时给出警告
git config --global core.safecrlf warn
通俗解释
```
