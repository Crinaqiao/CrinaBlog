---
title: 跨域：axios使用post请求带参数返回数据为空
tags:
  - axios
categories:
  - Bug
cover: https://picsum.photos/1080/1080?random=12211
feature: false
date: 2022-09-16 17:51:01
---
**问题**
运行后，用vue来做post数据请求，数据也可以发出去，但返回的一直是个空数组
**原因**
没有进行跨域请求
**解决方法**
发出的数据用qs处理一下发出
***步骤***
1.先安装qs
```
在命令行安装
npm install qs --save-dev
在你要请求数据的vue模块里
import qs from "qs";
```

2.2.进行引用和使用
```

<script>
import qs from "qs";
export default {
name: "HelloWorld",
data() {
return {
username: "",
password: "",
};
},
methods: {
login() {
let data = qs.stringify({
username: this.username,
password: this.password,
}); 
this.axios({
method: "post",
data,
url: "http://localhost:3000/login",
}).then((res) => {
console.log(res.data);
});
},
},
};
</script>

    ```

**参考**

CSDN链接：https://blog.csdn.net/weixin_45919499/article/details/123689482