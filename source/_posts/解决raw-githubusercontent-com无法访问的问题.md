---
title: 解决raw.githubusercontent.com无法访问的问题
tags:
  - Git
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=1234924
feature: false
date: 2022-11-01 12:03:59
---
# 解决raw.githubusercontent.com无法访问的问题
## 报错信息
```bash
Failed to connect to raw.githubusercontent.com port 443 after 86 ms: Couldn't connect to server
```
## 解决办法
- 打开`https://www.ipaddress.com`，
- 查找`raw.githubusercontent.com`，
- 找到相应的的`ipv4`地址
- 修改hosts文件
  ```bash
    sudo vim /etc/hosts
  ```
  ![](https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/202211011210602.png)
- 关闭终端，再试一次命令