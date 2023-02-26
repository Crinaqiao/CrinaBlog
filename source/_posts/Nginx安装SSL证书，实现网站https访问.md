---
title: Nginx安装SSL证书，实现网站https访问
tags:
  - Nginx
categories:
  - 运维
cover: https://picsum.photos/1080/1080?random=1457829
feature: false
date: 2022-08-30 17:28:06
---
# Nginx安装SSL证书，实现网站https访问

## 一、下载SSL证书，并且上传到Nginx配置文件所在目录下创建的cert文件夹中

![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202208301732836.png)
![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202208301738244.png)


## 二、修改Nginx配置文件
```json
server {

    listen 80;

    server_name jc-meet.cn;

    location / {

        root /home/blog/public/;

        index index.html;

    }

    #把http的域名请求转成https

    rewrite ^(.*)$ https://$host$1 permanent;

    }

  

    server{

        listen 443 ssl;

        server_name jc-meet.cn;

        ssl_certificate /usr/local/lighthouse/softwares/nginx/cert/1_jc-meet.cn_bundle.crt;

        ssl_certificate_key /usr/local/lighthouse/softwares/nginx/cert/2_jc-meet.cn.key;

        ssl_session_timeout 5m;

        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;

        #请按照以下套件配置，配置加密套件，写法遵循 openssl 标准。

        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;

        ssl_prefer_server_ciphers on;

        charset utf-8;

        location / {

            root   /home/blog/public/;

            index  index.html;

        }

    }
```