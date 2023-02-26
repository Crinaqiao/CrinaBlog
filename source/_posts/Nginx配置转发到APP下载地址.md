---
title: Nginx配置转发到APP下载地址
tags:
  - Nginx
categories:
  - 运维
cover: https://picsum.photos/1080/1080?random=1
feature: false
date: 2022-08-16 17:40:56
---
# Nginx配置转发到APP下载地址
```
server {
    listen 80;
    server_name 121.41.44.187;
    return 301 https://play.google.com/store/apps/details?id=com.jc.earner;
    }
```