---
title: 利用substring()和indexOf()从字符串中获取指定的字符
tags:
  - Java
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=191
feature: false
date: 2022-08-16 17:43:26
---
# 利用substring()和indexOf()从字符串中获取指定的字符

代码：

```java
@Test
    void spiltStrDemo() {
        /*
        * str.substring(4, 9); -->在str中截取从下标4开始（包含），到下标9之间的字符（不包含9）
        * str.indexOf("/");    -->返回str中“/”第一次出现时的下标
        * str.indexOf("/", 5); -->返回跳过str的前6个字符后，“/”第一次出现的下标。可以利用这个方法跳过前几个相同的字符
        * */

        /*演示数据准备，数据格式为：id/name/phoneNum*/
        String str = "id1/Riven/12346789999";

        /*第一种情况：知道具体字符下标，直接用substring()传入字符下标截取*/
        // 第一种情况假设我们已经知道了str的具体值，我们要从str中取出name->Riven
        String riven = str.substring(4, 9); // 这里传入R的下标4，再传入第二个“/”的下标9，拿到的就是Riven

        /*第二种情况：不知道字符下标，但是知道分割字符是“/”，可以用indexOf()获取字符“/”下标*/
        // 第二种情况我们获取id->id1
        String id = str.substring(0, str.indexOf("/"));

        /*善于思考的同学已经发现，第二种情况我们只能获取id，想拿后面其他数据就很难办了，因为我们有两个“/”，因此就有了第三种情况*/

        /*第三种情况：str中有多个相同字符，我们要跳过前几个字符获取后面的数据*/
        // 第三种情况我们想获取Riven，但是我们不知道Riven本身的下标
        // 首先，我们先拿到第一个“/”的下标
        int i = str.indexOf("/");
        // 然后我们拿到第二个“/”的下标,前两个“/”之间的数据就是我们的name字段了
        // indexOf()可以传两个参数，第一个是要寻找的子字符串，第二个是从哪个下标位置开始寻找，这里传入i+1就是跳过了第一个“/”之前的下标
        int i1 = str.indexOf("/", i + 1);
        String riven1 = str.substring(i + 1, i1);

        System.out.println("riven = " + riven);
        System.out.println("id = " + id);
        System.out.println("riven1 = " + riven1);
    }
```