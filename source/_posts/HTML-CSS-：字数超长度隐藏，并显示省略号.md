---
title: HTML | CSS ：字数超长度隐藏，并显示省略号
tags:
  - HTML
  - CSS
categories:
  - 开发笔记
cover: https://picsum.photos/1080/1080?random=901
feature: false
date: 2022-08-16 17:46:44
---
# HTML | CSS ：字数超长度隐藏，并显示省略号

```css
		width: 90%;      /**注意：如果使用百分比宽度，需要父级宽度是确定值**/
		overflow: hidden;  /**超出的文本隐藏**/
    text-overflow: ellipsis;   /**设置超长度部分显示省略号**/
    display: -webkit-box;  /**作为弹性伸缩盒子模型显示**/
    -webkit-line-clamp: 2;  /**设置最大显示两行**/
    -webkit-box-orient: vertical;   /**设置伸缩盒子的子元素排列方式--从上到下垂直排列**/
		
		/**如果只设置一行，那么需要加上这个属性**/
		white-space:nowrap; /**溢出不换行**/
```