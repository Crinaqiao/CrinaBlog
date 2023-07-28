---
title: 学习vue3
tags:
  - Vue
categories:
  - vue的学习
cover: https://picsum.photos/1080/1080?random=12214
feature: false
date: 2023-07-16 17:51:01
---
# reactive(),ref()
  1. 能在改变时触发更新的状态被称作是响应式的。我们可以使用 Vue 的 reactive() API 来声明响应式状态。由 reactive() 创建的对象都是 JavaScript Proxy，其行为与普通对象一样：
  2. reactive() 只适用于对象 (包括数组和内置类型，如 Map 和 Set)。而另一个 API ref() 则可以接受任何值类型。ref 会返回一个包裹对象，并在 .value 属性下暴露内部值。
  3. 注意我们在模板中访问的 message ref 时不需要使用 .value：它会被自动解包，让使用更简单。
   ```
  <h1>{{ message }}</h1>
  <p>count is: {{ counter.count }}</p>
   ```
# v-bind v-on
