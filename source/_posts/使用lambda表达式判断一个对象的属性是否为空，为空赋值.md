---
title: 使用lambda表达式判断一个对象的属性是否为空，为空赋值
tags:
  - Java
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=9211
feature: false
date: 2022-08-16 17:50:15
---
# 使用lambda表达式判断一个对象的属性是否为空，为空赋值

```java
//判断对象的color属性是否为空，为空加上默认颜色
.peek(p -> p.setColor(Opt.ofBlankAble(p.getColor()).orElse(DefaultConst.COLOR)))
```