---
title: vue 禁止遮罩滑动
author: Born to the sun
top: true
cover: false
toc: true
mathjax: true
date: 2020-12-28 16:15:10
keywords:
summary: vue 禁止遮罩滑动
tags: [vue]
categories: css
---
#### 遮罩层阻止默认滚动事件
vue中提供 @touchmove.prevent 方法可以完美解决这个问题。 
```html
<div class="child" @touchmove.prevent ></div>
```
#### vue同时还提供了其他的修饰符：
##### 1、.stop：阻止冒泡（通俗讲就是阻止事件向上级DOM元素传递）
```html
<a v-on:click.stop="doThis"></a> 
```

##### 2、.prevent：阻止默认事件的发生
```html
<form v-on:submit.prevent="onSubmit"></form> 
``
##### . capture：捕获冒泡，即有冒泡发生时，有该修饰符的dom元素会先执行，如果有多个，从外到内依次执行，然后再按自然顺序执行触发的事件。
```html
<div v-on:click.capture="doThis">...</div> 
```
##### 3、.self：将事件绑定到自身，只有自身才能触发，通常用于避免冒泡事件的影响

```html
<div v-on:click.self="doThat">...</div>
```
##### 4、.once：设置事件只能触发一次，比如按钮的点击等。

##### 5、.passive：该修饰符大概意思用于对DOM的默认事件进行性能优化，根据官网的例子比如超出最大范围的滚动条滚动的。

##### 6、.native：在父组件中给子组件绑定一个原生的事件，就将子组件变成了普通的HTML标签，不加'. native'事件是无法触 发的。