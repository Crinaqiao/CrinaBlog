---
title: ES6 export/import
tags:
  - JavaScript
  - ES6
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=39321
feature: false
date: 2022-08-16 18:04:54
---
# ES6 export/import

# 先说一个注意点：

如果代码运行报错：

```jsx
Uncaught SyntaxError: Cannot use import statement outside a module
```

这是因为：虽然谷歌浏览器(chrome 61之后)已经支持es6的Module了，但是不能简单的直接使用，我们需要在script标签上加一个：`type="module"`，或者我们可以使用babel 转成es5，这样也能愉快的使用import和export 。

```jsx
<script type="module">
improt ...
</script>
```

# export:

```jsx
// data.js
const obj = {
    first: {
        name: "张三"
    }
}
const haha = "哈哈哈哈哈";
export {obj,haha};

/*
使用export导出，那么导入的时候就需要指定变量名或者函数名
*/

// test.js
import {obj,haha} from "./data.js";

/*
或者使用import * 来导入，使用 as 取别名
*/
import * as all from "./data.js";
```

# export default：

> 从前面的例子可以看出，使用`import`命令的时候，用户需要知道所要加载的变量名或函数名，否则无法加载。但是，用户肯定希望快速上手，未必愿意阅读文档，去了解模块有哪些属性和方法。这时就可以使用export default。
> 

```jsx
// data.js
const obj = {
    first: {
        name: "张三"
    }
}
const haha = "哈哈哈哈哈";
export default {obj,haha};

/*
使用default导出，在导入的时候就可以不需要知道具体变量名或函数名，
直接导入就可以了，这里的object是我给的变量名
*/

// test.js
import object from "./data.js";
console.log(object.obj);
```

# import 和 import()：

```jsx
//import是静态加载的，而import()支持动态加载，并且是异步加载，CommonJS的require方法是同步加载

// data.js  用setTimeout模拟网络请求
function fn() {
    console.log("这是一个异步");
}
export {fn};

// test.js  import()是一个异步操作，会异步加载模块
import("./data.js").then(d => {
        console.log("模块加载完成")
    }).catch(err => {
        console.log(err)
    })
console.log("这是在import后面的输出语句");

// 输出结果：可以看到程序没有等待加载，而是先走了之后的打印操作，在加载模块完成后才执行了上面的打印操作
// 这是在import后面的输出语句
// 这是一个异步
```