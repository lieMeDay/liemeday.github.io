---
title: 时间格式转换
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-12-16 15:01:10
keywords:
summary: js各种时间相互转换
tags: [JavaScript]
categories: JavaScript
---
### 将秒转换成时分秒
```javascript
//将秒转换成时分秒
const formatSeconds = (a) => {
  var hh = parseInt(a / 3600);
  if (hh < 10) hh = "0" + hh;
  var mm = parseInt((a - hh * 3600) / 60);
  if (mm < 10) mm = "0" + mm;
  var ss = parseInt((a - hh * 3600) % 60);
  if (ss < 10) ss = "0" + ss;
  var length = hh + ":" + mm + ":" + ss;
  if (a > 0) {
    return length;
  } else {
    return "NaN";
  }
}
```
### 计算两个日期时间差 当前日期
```javascript
// 计算两个日期时间差 当前日期
const twoDateCom = (a, b) => {
  var d1 = new Date(a.replace(/-/g, "/")).getTime(); //将-转化为/，使用new Date
  var d2 = new Date().getTime()
  let cha = Math.round((d2 - d1) / 1000)
  if (b) {
    var d3 = new Date(b.replace(/-/g, "/")).getTime(); //将-转化为/，使用new Date
    cha = Math.round((d3 - d1) / 1000)
  }
  return cha
}
```
### 将时分秒的格式转换成秒的函数
```JavaScript
//将时分秒的格式转换成秒的函数
const hms = (time) => {
  var s = "";
  if (time != "" || time != null) {
    // console.log(time);
    var hour = time.split(":")[0];
    var min = time.split(":")[1];
    var sec = time.split(":")[2];
    s = Number(hour * 3600) + Number(min * 60) + Number(sec);
    return s;
  } else {
    return "";
  }
}
```
### 时间戳取时分秒
```JavaScript
// 时间戳取时分秒
const getCsfm = (data) => {
  var myDate = new Date(Number(data));
				// var year = myDate.getFullYear(); //获取当前年
				// var mon = myDate.getMonth() + 1; //获取当前月
				// var date = myDate.getDate(); //获取当前日
        var hours = myDate.getHours(); //获取当前小时
        hours=hours<10?'0'+hours:hours
				var minutes = myDate.getMinutes(); //获取当前分钟
        minutes=minutes<10?'0'+minutes:minutes
				var seconds = myDate.getSeconds(); //获取当前秒
        seconds=seconds<10?'0'+seconds:seconds
				var now = hours + ":" + minutes + ":" + seconds;
				return now;
}
```
### 获取两个日期之间相隔的所有日期
```JavaScript
// 获取两个日期之间相隔的所有日期
function getDayAll(starDay, endDay) {

  var arr = [];
  var dates = [];
  // 设置两个日期UTC时间
  var db = new Date(starDay.replace(/-/g, "/"));
  var de = new Date(endDay.replace(/-/g, "/"));

  // 获取两个日期GTM时间
  var s = db.getTime() - 24 * 60 * 60 * 1000;
  var d = de.getTime() - 24 * 60 * 60 * 1000;

  // 获取到两个日期之间的每一天的毫秒数
  for (var i = s; i <= d;) {
    i = i + 24 * 60 * 60 * 1000;
    arr.push(parseInt(i))
  }

  // 获取每一天的时间  YY-MM-DD
  for (var j in arr) {
    var time = new Date(arr[j]);
    var year = time.getFullYear(time);
    var mouth = (time.getMonth() + 1) >= 10 ? (time.getMonth() + 1) : ('0' + (time.getMonth() + 1));
    var day = time.getDate() >= 10 ? time.getDate() : ('0' + time.getDate());
    var YYMMDD = year + '-' + mouth + '-' + day;
    dates.push(YYMMDD)
  }

  return dates
}
```