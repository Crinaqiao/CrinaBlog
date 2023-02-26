---
title: npm xxx command not found和hexo在后台运行的解决办法
tags:
  - npm
  - hexo
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=123942
feature: false
date: 2022-08-16 19:22:36
---
# 解决npm找不到命令的问题
```bash
mkdir /.npm-global
npm config set prefix './npm-global'
vim /.profile
source /.profile
```
> .profile文件如下：
> export PATH=/.npm-global/bin:$PATH
> 编辑完成后重新安装找不到的包就可以解决问题

# 让hexo在后台运行
> 安装pm2
```bash
npm  install -g pm2
```
> 写一个运行脚本，在博客根目录下面创建一个hexo_run.js
```JavaScript
//run
const { exec } = require('child_process')
exec('hexo server',(error, stdout, stderr) => {
        if(error){
                console.log('exec error: ${error}')
                return
        }
        console.log('stdout: ${stdout}');
        console.log('stderr: ${stderr}');
})
```
> 运行命令
```bash
pm2 start hexo_run.js
```