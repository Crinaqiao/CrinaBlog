---
title: Android gradle换源和gradle版本对应表
tags:
  - Android
  - Gradle
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=128334
feature: false
date: 2022-10-08 16:24:14
---
# 换源
```gradle
maven { url 'https://maven.aliyun.com/nexus/content/repositories/google' }
maven { url 'https://maven.aliyun.com/nexus/content/groups/public' }
maven { url 'https://maven.aliyun.com/nexus/content/repositories/jcenter'}
google()
mavenCentral()
jcenter()
maven { url "https://jitpack.io" }
```

# Gradle版本对应表
https://developer.android.google.cn/studio/releases/gradle-plugin

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202210081631609.png)