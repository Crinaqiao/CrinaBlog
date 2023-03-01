---
title: 前端HTML面经
tag:
    - html
categories:
    - 面经
cover: https://picsum.photos/1080/1080?random=12212
feature: false
date: 2022-06-16 17:00:01
---

<h1>这是我参与「第五届青训营 」伴学笔记创作活动的第 10天</h1>
    <h2>1.src和herf的区别</h2>
    <p>src是对资源的引用，所指向的内容会嵌入到当前的标签。会暂停对文档其他内容的加载，直到src所指向的文件内容加载完，所以一般放在js底部。<br>而herf是超文本的引用，不会暂停当前文档的处理，是同时处理的。</p>
    <h2>2.html标签语义化</h2>
    
```
<header></header>  头部

<nav></nav>  导航栏

<section></section>  区块（有语义化的div）

<main></main>  主要区域

<article></article>  主要内容

<aside></aside>  侧边栏

<footer></footer>  底部
```

<h2>3.defer和async的区别</h2>
执行顺序：defer按照顺序执行。async不能保证加载顺序。
脚本执行：async的文档的加载和执行和脚本的加载和执行,即异步进行.defer是只有加载同时进行,脚本等到文档解析完才执行.
<h2>4.mata标签</h2>
`meta` 标签由 `name` 和 `content` 属性定义，<b>用来描述网页文档的属性</b>，比如网页的作者，网页描述，关键词等，除了HTTP标准固定了一些`name`作为大家使用的共识，开发者还可以自定义name。
1. charset--html文档的编码类型

`<meta charset="UTF-8" >`

2. keywords--页面关键词

`<meta name="keywords" content="关键词" />`

3.description--页面描述

`<meta name="description" content="页面描述内容" />`

4.refresh--页面重定向和刷新

`<meta http-equiv="refresh" content="0;url=" />
`

5.viewport--适配移动端,可控制视口的大小和比例.

`<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
`

<h2>5.搜索引擎方式:</h2>

`<meta name="robots" content="index,follow" />
`

`content` 参数有以下几种：

-   `all`：文件将被检索，且页面上的链接可以被查询；
-   `none`：文件将不被检索，且页面上的链接不可以被查询；
-   `index`：文件将被检索；
-   `follow`：页面上的链接可以被查询；
-   `noindex`：文件将不被检索；
-   `nofollow`：页面上的链接不可以被查询。
<h2>6.HTML5</h2>
<h3>1.媒体标签</h3>

- audio-音频
 `
 <audio src='' controls autoplay loop='true'></audio>
`

    -   controls 控制面板
    -   autoplay 自动播放
    -   loop=‘true’ 循环播放
    
- vedio-视频
`<video src='' poster='imgs/aa.jpg' controls></video>`
    -   poster：指定视频还没有完全下载完毕，或者用户还没有点击播放前显示的封面。默认显示当前视频文件的第一针画面，当然通过poster也可以自己指定。
    -   controls 控制面板
    -   width
    -   height
- source-因为浏览器对视频格式支持程度不一样，为了能够兼容不同的浏览器，可以通过source来指定视频源。

```
<video>
<source src='aa.flv' type='video/flv'></source>
<source src='aa.mp4' type='video/mp4'></source>
</video>
```
<h3>2.表单</h3>

- **表单类型：**
    -   email ：能够验证当前输入的邮箱地址是否合法
    -   url ： 验证URL
    -   number ： 只能输入数字，其他输入不了，而且自带上下增大减小箭头，max属性可以设置为最大值，min可以设置为最小值，value为默认值。
    -   search ： 输入框后面会给提供一个小叉，可以删除输入的内容，更加人性化。
    -   range ： 可以提供给一个范围，其中可以设置max和min以及value，其中value属性可以设置为默认值
    -   color ： 提供了一个颜色拾取器
    -   time ： 时分秒
    -   data ： 日期选择年月日
    -   datatime ： 时间和日期(目前只有Safari支持)
    -   datatime-local ：日期时间控件
    -   week ：周控件
    -   month：月控件
- **表单属性:**
    - placehoder:提示信息
    - autofocus:自动获取焦点
    - autocomplete="on/off",(表单必须提交过+有name属性)
    - required:输入框不能为空.
    - pattern="",里面写正则模式,例如手机号.
    - multiple:可以选择多个文件或者多个邮箱.
    - form:form表单的id
 
-   **表单事件**
    -  oninput:内容变化触发
    -  oninvalid:验证不通过触发
    
<h3 >3.  进度条,度量器   </h3>

- process标签:表示任务的进度.（IE、Safari不支持），max用来表示任务的进度，value表示已完成多少.

- meter属性:用来显示剩余容量.（IE、Safari不支持）
    -   high/low：规定被视作高/低的范围
    -   max/min：规定最大/小值
    -   value：规定当前度量值

  



