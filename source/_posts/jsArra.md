---
title: 数组方法
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-06-30 18:50:40
keywords:
summary: js把一个数组内容插入到另一个数组的指定位置
tags: [JavaScript]
categories: JavaScript
---
js把一个数组内容插入到另一个数组的指定位置
```javaScript
let arr1 = ['a', 'b', 'c']; 
let arr2 = ['1', '2', '3']; 
// 把arr2 变成一个适合splice的数组（包含splice前2个参数的数组）
arr2.unshift(2, 0); // ------------------ 这里的数字控制插入的位置-------------------------
console.log(arr2); 
//[2, 0, "1", "2", "3"]
Array.prototype.splice.apply(arr1, arr2); 
console.log(arr1); 
//["a", "b", "1", "2", "3", "c"]

```