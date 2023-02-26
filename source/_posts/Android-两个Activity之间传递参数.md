---
title: Android 两个Activity之间传递参数
tags:
  - Android
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=13294
feature: false
date: 2022-10-08 15:09:55
---
# 需求
> 例如：我们要把一个参数从'MainActivity'传递到'web_page'
# 实现代码
```Java
  /*MainActivity 发送*/
  Intent intent = new Intent(MainActivity.this, web_page.class);
  intent.putExtra("BliIp", dataStr.data.country);
  startActivity(intent);
  
  /*web_page 接收*/
  Intent intent = getIntent();
  bliIp = intent.getStringExtra("BliIp");
```