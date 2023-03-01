---
title: 引入element无效
tag : Vue
categories: Bug
cover: https://picsum.photos/1080/1080?random=12212
feature: false
date: 2022-05-13 17:00:01

---

** 1.布尔值类型前面要加冒号 **
``` 
:enterable="false" 

```

** 2.格式问题 **
```

import Vue from 'vue'
//去掉el的开头，-换成大写
import { Button, Form, Input, FormItem, Container,
  Main, Aside, Header, Menu,MenuItemGroup, Submenu, MenuItem,Breadcrumb,BreadcrumbItem } from 'element-ui'
//这里不能写数组，必须分开。
Vue.use(Button)

```