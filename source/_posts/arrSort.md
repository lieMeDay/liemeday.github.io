---
title: js数组对象排序
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-11-28 15:01:10
keywords:
summary: sort排序
tags: [JavaScript]
categories: JavaScript
---
### 普通排序
```javascript
var arr = ["a", "b", "A", "B"];
arr.sort();
console.log(arr);//["A", "B", "a", "b"]
```

### 数组对象
利用数组api ——> sort来进行排序
```javascript
var person = [{name:"Rom",age:12},{name:"Bob",age:22},{name:"Ma",age:5},{name:"Tony",age:25}]
 
person.sort((a,b)=>{ return a.age-b.age})//升序
 
person.sort((a,b)=>{ return b.age-a.age})//降序
```