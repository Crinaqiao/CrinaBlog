---
title: mysql不是内部或外部命令，也不是可运行的程序或批处理文件
tag:
    - node.js
categories:
    - Bug
cover: https://picsum.photos/1080/1080?random=122110
feature: false
date: 2022-06-18 18:00:01
---

**出现原因：**
通过form格式请求接口，数据先转码，以某种未知字符集，会对汉字做处理，其他类型的值不受影响。
**解决方案：**
在header中对Content-Type的值再次进行定义“application/x-www-form-urlencoded; charset=UTF-8”

**参考**
http://t.csdn.cn/pctUs
