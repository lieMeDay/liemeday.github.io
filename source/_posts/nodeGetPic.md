---
title: nodeJs爬取图片
author: Born to the sun
top: true
cover: false
toc: true
mathjax: true
date: 2021-01-05 15:30:10
keywords:
summary: 简单的nodeJs爬取图片 demo
tags: [nodeJs,JavaScript]
categories: nodeJs
---
简单的nodeJs爬取图片 小样例
### 1、新建node项目
npm init -y
-y 的含义：yes的意思，在init的时候省去了敲回车的步骤，生成的默认的package.json

### 2、安装模块
爬取图片所需要的模块
 * request request模块让http请求变的更加简单。(作为客户端，去请求、抓取另一个网站的信息)
 * cheerio cheerio 是一个 jQuery Core 的子集，其实现了 jQuery Core 中浏览器无关的 DOM 操作 API
 request cheerio 需要npm 下载
 * fs 自带 操作文件读写

### 3、编写抓取图片代码
#### 1、新建 app.js
```JavaScript
//引入模块
const cheerio = require('cheerio');
const fs = require('fs');
const request = require('request');

// 获取页面信息
function start(url) {
    request(url, function (err, res, body) {
        if (!err && res.statusCode == 200) {
            findImg(body, saveImgFile);
        }
    })
}
// url 为页面的url
start('url')

// 页面节点解析
function findImg(dom,callback) {
 let $ = cheerio.load(dom);
//  页面节点 找到img 标签 each 循环
 $('img').each((index,dom)=>{
 let imgSrc = $(dom).attr('src');
 // 获取图片路径
 callback(imgSrc,index);
 })
}

function saveImgFile(src, index) {
    console.log(src,index)
    let ext = src.split('.').pop() //图片类型 png jpg  pop() 方法用于删除并返回数组的最后一个元素。
    let imgName = index + '.' + ext
    // if (src.indexOf('http') < 0) src = 'http:' + src
    // src 路径需确保为完整路径
    // 新建pic 文件夹 保存到文件夹下
    request(src).pipe(fs.createWriteStream('./pic/' + imgName)) // 下载文件到本地
}

// 调用start  url 为页面的url
start('http://www.netbian.com/index.htm')
```
目录 ：page.json ，app.js ，pic文件夹
#### 2、运行
node app.js

注：<font color=#999 size=1px>最最简单的图片抓取方法，大部分页面都支持</font>