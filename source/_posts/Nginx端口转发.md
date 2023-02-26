---
title: Nginx端口转发
tags:
  - Nginx
categories:
  - 运维
cover: https://picsum.photos/1080/1080?random=112
feature: false
date: 2022-08-16 17:39:10
---
# 监听不同域名的端口，并转发
``` json
server
    {
      listen 9744;
      server_name 43.154.174.219|as41.store|yl13.fit|hio.wiki;
      index index.html;
      root /home/node-websocket-Chatroom/dist;

      location ^~ /socket.io/ {
        proxy_pass  http://43.154.174.219:9745;
        proxy_set_header Host $proxy_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      }

        access_log  /www/wwwlogs/webChatRoom.log;
    }
```
