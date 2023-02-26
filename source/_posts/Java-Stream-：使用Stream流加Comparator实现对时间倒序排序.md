---
title: Java | Stream ：使用Stream流加Comparator实现对时间倒序排序
tags:
  - Java
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=381
feature: false
date: 2022-08-16 17:49:08
---
# Java | Stream ：使用Stream流加Comparator实现对时间倒序排序

```java
.sorted(Comparator.comparing(ProjectDynamic::getGmtCreate).reversed())
```