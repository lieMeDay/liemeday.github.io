---
title: 小程序button去掉默认样式
author: Born to the sun
top: false
cover: false
toc: false
mathjax: true
date: 2021-01-06 12:02:01
keywords:
summary: 微信小程序修改radio组件自定义选中、未选中样式
tags: [小程序,JavaScript]
categories: 小程序
---
![1](https://img-blog.csdnimg.cn/20210105163337499.png)
```javascript
// 在本地用户文件目录下创建一个文件 hello.txt，写入内容 "hello, world"
const fs = wx.getFileSystemManager()
fs.writeFileSync(`${wx.env.USER_DATA_PATH}/hello.txt`, 'hello, world', 'utf8')
```
```javascript
// 写入图片
fsm.writeFile({
    filePath:`${wx.env.USER_DATA_PATH}/a.jpg`,
    data: buffer,
    encoding: 'binary',
    success() {
    // resolve(filePath);
    wx.getImageInfo({
        src: `${wx.env.USER_DATA_PATH}/a.jpg`,
        success: function (res) {
        console.log(res)
        resolve(res);
        },
    })
 ```
[小程序API文档介绍](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/file-system.html)