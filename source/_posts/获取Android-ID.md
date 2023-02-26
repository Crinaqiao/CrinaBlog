---
title: 获取Android ID
tags:
  - Android
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=1892384
feature: false
date: 2022-10-08 15:44:32
---
# 一、需求场景
> 需要记录用户的设备唯一性，这里使用Android ID的方式，但其实这种方法并不完全唯一。ANDROID_ID是设备的系统首次启动时随机生成的一串字符，由16个16进制数（64位）组成，基本上还是可以保证唯一性的。ANDROID_ID的获取门槛是最低的，不需要任何权限，但ANDROID_ID也存在一些缺点，就是无法保证稳定性，root、刷机或恢复出厂设置都会导致设备的ANDROID_ID发生改变。


# 二、实现代码
```Java
  String ANDROID_ID = Settings.System.getString(getContentResolver(), Settings.Secure.ANDROID_ID);
```
