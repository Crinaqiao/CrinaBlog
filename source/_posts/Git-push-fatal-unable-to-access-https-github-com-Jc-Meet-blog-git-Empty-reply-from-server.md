---
title: >-
  Git push fatal: unable to access https://github.com/xxx/xxx.git/: Empty
  reply from server
tags:
  - Git
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=19834857
feature: false
date: 2022-11-01 12:45:50
---
## 报错
```bash
  Git push fatal: unable to access https://github.com/xxx/xxx.git/: Empty reply from server
```

## 解决办法
1. 查看git配置
  ```bash
    git config --global -l  
  ```
2. 取消代理信息的配置
  ```bash
    git config --global --unset http.proxy
    git config --global --unset https.proxy
  ```
  再次查看git配置
3. 重新push
   ```bash
    git remote rm origin    #删除之前错误建立的远程仓库防止出错
    git remote add origin https://github.com/....   #此处修改为自己的项目地址
    git push origin master //推至远程仓库，应该会要求输入用户名密码
   ```

