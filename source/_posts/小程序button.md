---
title: 小程序button去掉默认样式
author: Born to the sun
top: false
cover: false
toc: false
mathjax: true
date: 2021-01-06 10:10:10
keywords:
summary: 微信小程序修改radio组件自定义选中、未选中样式
tags: [小程序,css]
categories: 小程序
---
/* 去除button默认样式 */

button::after {
border: none;

}

button {
background-color: transparent;

padding-left: 0;

padding-right: 0;

line-height:inherit;

}

button {
border-radius:0;

}