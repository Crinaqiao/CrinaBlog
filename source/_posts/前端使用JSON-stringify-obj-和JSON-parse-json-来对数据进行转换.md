---
title: 前端使用JSON.stringify(obj)和JSON.parse(json)来对数据进行转换
tags:
  - JavaScript
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=1221
feature: false
date: 2022-08-16 17:51:01
---
# 前端使用JSON.stringify(obj)和JSON.parse(json)来对数据进行转换

**JSON 是用于存储和传输数据的格式。
JSON 通常用于服务端向网页传递数据 。**

在开发中，我们经常会需要对数据进行转化处理，在JavaScript中提供了两个函数：**JSON.parse()和JSON.stringify()**。

# **JSON.parse() 方法用于将一个 JSON 字符串转换为对象。**

**语法**：JSON.parse(text,function)
这个方法可以传两个参数：

- 第一个参数是要转换的json字符串。
- 第二个参数可以传一个函数（也可以不传）。对象中的每个成员都会调用这个函数。

# **JSON.stringify() 方法用于将对象或数组转换为 JSON 字符串。**

**语法**：JSON.stringify(value, replacer, space)
这个方法可以传三个参数：

- value是要转换的对象或数组，是必须的。
- replacer可以是函数或数组，如果参入函数，则 JSON.stringify 将调用该函数，并传入每个成员的键和值。使用返回值而不是原始值。如果此函数返回 undefined，则排除成员。根对象的键是一个空字符串：""。如果replacer传入是一个数组，则仅转换该数组中具有键值的成员。成员的转换顺序与键在数组中的顺序一样。
- space为文本添加缩进、空格和换行符，如果 space 是一个数字，则返回值文本在每个级别缩进指定数目的空格，如果 space 大于 10，则文本缩进 10 个空格。space 也可以使用非数字，如：\t。