---
title: 小程序radio组件样式
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-12-29 10:10:10
keywords:
summary: 微信小程序修改radio组件自定义选中、未选中样式
tags: [小程序]
categories: css
---
根据自己项目要求修改颜色按钮大小即可
```css
radio .wx-radio-input {
  /* 自定义样式.... */
  height: 24rpx;
  width: 24rpx;
  margin-top: -4rpx;
  border-radius: 50%;
  border: 2rpx solid #999;
  background: transparent;
}


radio .wx-radio-input.wx-radio-input-checked::before {
  border-radius: 50%; /* 圆角 */
  width: 28rpx; /* 选中后对勾大小，不要超过背景的尺寸 */
  height: 28rpx; /* 选中后对勾大小，不要超过背景的尺寸 */
  line-height: 28rpx;
  text-align: center;
  font-size: 30rpx; /* 对勾大小 30rpx */
  color: #fff; /* 对勾颜色 白色 */
  background: #0076fe;
  transform: translate(-50%, -50%) scale(1);
  -webkit-transform: translate(-50%, -50%) scale(1);
}
```