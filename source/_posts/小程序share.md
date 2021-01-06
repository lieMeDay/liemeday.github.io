---
title: 小程序点击按钮分享
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2021-01-06 14:02:01
keywords:
summary: 小程序通过点击按钮分享
tags: [小程序,JavaScript]
categories: 小程序
---
### wxml
```html
<button open-type="share">
    <view>分享给好友</view>
</button>
```
### JS
```javascript
  onShareAppMessage: function (res) {
    if (res.from === 'button') {
      console.log(res.target)
    }
    return {
      title: "分享给好友",
      path: '/pages/share/share',
      imgurl:'',
      success: function (res) {
        console.log('成功', res)
      }
    }
  },

```