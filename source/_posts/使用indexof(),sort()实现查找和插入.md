---
title: 使用indexof(),sort()实现查找和插入
tags:
  - JavaScript
categories:
  - 算法
cover: https://picsum.photos/1080/1080?random=12218
feature: false
date: 2022-09-16 17:51:01
---
### 解题思路
1.先用nums.Indexof(target)判断target是否在Nums数组中，如果是则返回target所在下标，如果不在返回-1
2.如果返回-1,则用Nums.push(target)将target加到数组中。
3.再使用nums.sort((a,b)=>a-b)从小到大排序数组
4.再次利用indexof()返回target所在下标

### 代码

```javascript
    var searchInsert = function (nums, target) {
        var result = nums.indexOf(target)
        console.log(result)
        if (result === -1) {
            nums.push(target)
            nums.sort((a,b)=>a-b)
            result=nums.indexOf(target)

        }
       
            return result
        
    };

```