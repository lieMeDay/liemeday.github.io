---
title: 获取中心点和缩放级别
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-06-30 18:50:40
keywords:
summary: js获取地图中心点和对应展示缩放级别
tags: [JavaScript]
categories: JavaScript
---
### 获取中心点和缩放级别
```JavaScript
// 获取中心点和缩放级别
let getCenterAndZoom=(maxJ, minJ, maxW, minW,i)=>{
  var centerLongitude = ((parseFloat(minJ) + parseFloat(maxJ)) / 2).toFixed(5);
    var centerLatitude = ((parseFloat(minW) + parseFloat(maxW)) / 2).toFixed(5);
    let zoom = getCenterPoint(maxJ, minJ, maxW, minW)
    if(i){
      zoom+=1
    }
    //如果经纬度在array中不是数字类型，需要转化为数字类型进行计算，如果是可以去掉parseFloat处理
    //console.log(centerLongitude+"kkk"+centerLatitude);
    return [centerLongitude, centerLatitude, zoom];
}
let getCenterPoint=(maxJ, minJ, maxW, minW)=>{ //通过经纬度获取中心位置和缩放级别
  let dd=getDistance(maxW,maxJ,minW,minJ)
  var diffArr =  [0.01, 0.02, 0.05, 0.05, 0.1, 0.2, 0.5, 1, 2, 5, 10, 20, 50, 50, 100, 200, 500, 1000]
  for (var i = 0; i < diffArr.length; i++) {
    if (diffArr[i] - dd > 0) {
      // 18 - i + 3
      return 19 - i + 3; //之所以会多4，是因为地图范围常常是比例尺距离的10倍以上。所以级别会增加4。
    }
  }
}
// 根据两点经纬度计算距离
const getDistance = (lat1, lng1, lat2, lng2) => {
  var radLat1 = lat1 * Math.PI / 180.0;
  var radLat2 = lat2 * Math.PI / 180.0;
  var a = radLat1 - radLat2;
  var b = lng1 * Math.PI / 180.0 - lng2 * Math.PI / 180.0;
  var s = 2 * Math.asin(Math.sqrt(Math.pow(Math.sin(a / 2), 2) +
    Math.cos(radLat1) * Math.cos(radLat2) * Math.pow(Math.sin(b / 2), 2)));
  s = s * 6378.137; // EARTH_RADIUS;
  s = Math.round(s * 10000) / 10000;
  return s;
}
```