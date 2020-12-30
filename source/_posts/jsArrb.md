---
title: 数组方法
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-06-30 18:50:40
keywords:
summary: 输入一个数值，返回数组项最接近的一项
tags: [JavaScript]
categories: JavaScript
---

### 输入一个数值，返回数组项最接近的一项
```JavaScript
const lookupNear = (array, value) => {
  // 将原数组复制，不会影响原数组
  let arr = array.concat([]);
  arr.push(value);
  // 数据排序
  arr.sort((a, b) => {
    return a - b;
  });
  let index = arr.indexOf(value);
  // 当前项在数组第一项 / 最后一项，返回当前项的后一项 / 前一项
  if (index === 0) {
    // return arr[index + 1];
    return index+1
  } else if (index === array.length - 1) {
    // return arr[index - 1];
    return index-1
  }
  //   console.log(arr)
  // 当前项和前一项或者后一项比较，返回差值小的项
  //   console.log(arr[index - 1],arr[index],arr[index + 1])
  let resultIndex =
    arr[index] - arr[index - 1] > arr[index + 1] - arr[index] ?
    index + 1 :
    index - 1;
  //   console.log( arr[resultIndex],resultIndex)
  // return arr[resultIndex];
  return resultIndex
}
```