---
title: scss基础用法
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-12-28 15:01:10
keywords:
summary: scss基础用法 语法
tags: [css,html,scss,vue]
categories: css
---
## 安装
```javaScript
​npm install node-sass --save-dev        //安装node-sass 
npm install sass-loader@7.3.1 --save-dev      //安装sass-loader 
npm install style-loader --save-dev         //安装style-loader
```
### 简单用法
#### ​& 都代指父类
![](https://liemeday.github.io/blogPic/20201228150110/1.jpg)
变量是以 $ 开头的，可以是颜色，长度，数值，等等。

像 js 的变量一样，scss 的变量也是有作用域的，也就是说内部声明的变量是无法在外面使用的，如果想让内部的变量在外部可访问，需要在变量值后面添加 !global 声明。
![](https://liemeday.github.io/blogPic/20201228150110/2.jpg)
将变量直接嵌入字符串，需要用 #{ 变量 } （类似 ES6 中模板字符串中的 ${ 变量 }）
![](https://liemeday.github.io/blogPic/20201228150110/3.jpg)
如果 url() 传入的参数是有效的带引号的url，sass不会处理它，但还可以往其中插入变量，如果不是有效的带引号的 url，带有方法或变量的，sass就把它当成正常的方式识别
![](https://liemeday.github.io/blogPic/20201228150110/4.jpg)
#### @mixin 定义一个类或方法，在其它地方通过 @include 引用这个方法或类。

![](https://liemeday.github.io/blogPic/20201228150110/5.jpg)
#### @extend 继承

​不能继承 @extend .danger.text 这种连续组合的类，应该写为 @extend .danger, .text
![](https://liemeday.github.io/blogPic/20201228150110/6.jpg)
#### 颜色 透明饱和度
![](https://liemeday.github.io/blogPic/20201228150110/7.jpg)
![](https://liemeday.github.io/blogPic/20201228150110/8.jpg)
#### 方法以 @function 开头，以 @return 结尾，也就是说，方法的定义，必须要有返回值
![](https://liemeday.github.io/blogPic/20201228150110/9.jpg)
![](https://liemeday.github.io/blogPic/20201228150110/10.jpg)