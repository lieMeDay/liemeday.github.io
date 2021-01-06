---
title: js循环方法 -- for
author: Born to the sun
top: true
cover: false
toc: true
mathjax: true
date: 2020-11-28 15:01:10
keywords:
summary: for循环方法
tags: [JavaScript,es6]
categories: JavaScript
---
### 1.for循环
最基本的循环方式，不多说。前端js中，这种最基本的循环才是速度最快的，效率最高的
```javascript
let arr = [1,2,3];
for (let i=0; i<arr.length; i++){
 console.log(i,arr[i])
}
```
### 2.for in循环
for in循环是用来遍历对象的。要知道JavaScript对象的所有属性都是字符串，不过属性对应的值可以是任意数据类型。（注意：遍历时不仅能读取对象自身上面的成员属性，也能遍历出对象的原型属性）
```javascript
let obj = {a:1, b:2, c:3};
for (let prop in obj) {    //prop指对象的属性名
console.log(prop, obj[prop]);
}
// 输出:
// a,1
// b,2
// c,3
```
for in同样可以用来循环数组,但是不推荐这么做。由于Array也是对象，而它的每个元素的索引被视为对象的属性，因此，for in循环可以直接循环出Array的索引，但得到的是String而不是Number，所以一旦你想用这个index去进行计算，就会出错。

```javascript
for (var index in myArray) { // 不推荐这样
console.log(myArray[index]);
}
```
### 3. forEach循环
没什么好说的，看例子。(注意：forEach循环里面没办法用break跳出循环。而且在IE中无法实现，需要做兼容处理。)

```javascript
let arr = ['123','qwewq','sfds'];
myArray.forEach(function (value, index) {
    console.log(value,index);
});
//输出
//"123",1
//"qwewq",2
//"sfds",3
```
### 4.for of循环
作为ES6新增的循环方法，个人觉得相当好用，而且方便。这个方法避开了for-in循环的所有缺陷。而且，它可以正确响应break、continue和return语句。

```javascript
//循环数组
let arr = ['123','qwewq','sfds'];
for(let item of arr){
    console.log(item);    //item指的的就是数组每一项的值。不是索引。
}
//输出
//'123'
//'qwewq'
//'sfds'
```
for-of循环不仅支持数组，还支持大多数类数组对象，例如DOM NodeList对象。但是for of也有一个致命伤，就像例子看到的，没有索引。对，这是优点也是缺点。遍历数组对象，直接就是item.属性(或者item[属性]),而不用像for循环那样arr[index].属性(arrindex)。但是你有的时候真的就得用到index。不好意思，只能把数组转成Map()。但我觉得真的需要用到index，还是换成forEach吧

```javascript
//遍历字符串
let name = 'Asher';
for (let char of name){
    console.log(char);         //A s h e r
}
```
### 5.map
map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。

```javascript
let arr = [1,2,3];
let tt = arr.map(function(i){
//  console.log(i)
 return i*2;
})
// [2,4,6]
```
### 6.filter
filter 方法是 Array 对象内置方法，它会返回通过过滤的元素，不改变原来的数组。

```javascript
let arr = [1,2,3];
let tt = arr.filter(function(i){
 return i>1;
})
// [2,3]
// 或
tt=arr.filter（（v）=>v>1）
```
### 7.some
some() 方法用于检测数组中的元素是否满足指定条件（函数提供）,返回 boolean 值，不改变原数组。

```javascript
let arr = [1,2,3];
let tt = arr.some(function(i){
 return i>1;
})
// true
```
### 8.every
every() 方法用于检测数组所有元素是否都符合指定条件（通过函数提供），返回 boolean 值，不改变原数组。

```javascript
let arr = [1,2,3];
let tt = arr.some(function(i){
 return i>1;
})
// 检测数组中元素是否都大于1
// false
```
### 9.reduce
reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。

```javascript
let arr = [1,2,3];
let ad = arr.reduce(function(i,j){
 return i+j;
})
```
// 6
可以使用reduce去重

```javascript
let person = [
     {id: 0, name: "小明"},
     {id: 1, name: "小张"},
     {id: 2, name: "小李"},
     {id: 3, name: "小孙"},
     {id: 1, name: "小周"},
     {id: 2, name: "小陈"},   
];

let obj = {};

person = person.reduce((cur,next) => {
    obj[next.id] ? "" : obj[next.id] = true && cur.push(next);
    return cur;
},[])
```
### 10.其他
还有while，do . . . while ，switch等