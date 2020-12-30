---
title: flex基础用法
author: Born to the sun
top: false
cover: false
toc: true
mathjax: true
date: 2020-12-28 15:10:10
keywords:
summary: flex基础用法,布局
tags: [css,html]
categories: css
---
## flex布局属性

wps  文档  <https://kdocs.cn/l/ceEQBvIDZHxO>
FlexiableBox即是弹性盒，用来进行弹性布局，一般跟rem（rem伸缩布局（转））连起来用比较方便，flexbox负责处理页面布局，然后rem处理一些flex顾及不到的地方（rem伸缩布局主要处理尺寸的适配问题），布局还是要传统布局的。
![](https://liemeday.github.io/blogPic/20201228151010/1.webp)
布局的传统解决方案，基于<font color=blue>盒状模型</font>，依赖<font color=blue>display</font>属性+<font color=blue>position</font> 属性 +<font color=blue>float</font>属性。它对于那些特殊布局非常不方便，比如，<font color=blue>垂直居中</font>就不容易实现。
![](https://liemeday.github.io/blogPic/20201228151010/2.webp)
2009年，W3C提出了一种新的方案—-Flex布局，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有浏览器的支持，这意味着，现在就能很安全地使用这项功能。
![](https://liemeday.github.io/blogPic/20201228151010/3.webp)

Flex布局将成为未来布局的首选方案。

### 一、Flex布局是什么？

Flex是Flexible Box的缩写，意为”弹性布局”，用来为盒状模型提供最大的灵活性。

任何一个容器都可以指定为Flex布局。

.box{display:flex;}

行内元素也可以使用Flex布局。

.box{display:inline-flex;}

Webkit内核的浏览器，必须加上-webkit前缀。

.box{display:-webkit-flex;/* Safari */display:flex;}

注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。

### 二、基本概念

采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称”项目”。
![](https://liemeday.github.io/blogPic/20201228151010/4.webp)
容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

### 三、容器的属性

以下6个属性设置在容器上。
flex-direction
flex-wrap
flex-flow
justify-content
align-items
align-content
#### 3.1 flex-direction属性
flex-direction属性决定主轴的方向（即项目的排列方向）。
.box{flex-direction:row|row-reverse|column|column-reverse;}
![](https://liemeday.github.io/blogPic/20201228151010/5.webp)
它可能有4个值。

row（默认值）：主轴为水平方向，起点在左端。
row-reverse：主轴为水平方向，起点在右端。
column：主轴为垂直方向，起点在上沿。
column-reverse：主轴为垂直方向，起点在下沿。
#### 3.2 flex-wrap属性
默认情况下，项目都排在一条线（又称”轴线”）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。
![](https://liemeday.github.io/blogPic/20201228151010/6.webp)
.box{flex-wrap:nowrap|wrap|wrap-reverse;}
它可能取三个值。

（1）nowrap（默认）：不换行。
![](https://liemeday.github.io/blogPic/20201228151010/7.webp)
（2）wrap：换行，第一行在上方。
![](https://liemeday.github.io/blogPic/20201228151010/8.webp)

（3）wrap-reverse：换行，第一行在下方。
![](https://liemeday.github.io/blogPic/20201228151010/9.webp)
#### 3.3 flex-flow

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。

.box{flex-flow:||;}

#### 3.4 justify-content属性

justify-content属性定义了项目在主轴上的对齐方式。

.box{justify-content:flex-start|flex-end|center|space-between|space-around;}
![](https://liemeday.github.io/blogPic/20201228151010/10.webp)
它可能取5个值，具体对齐方式与轴的方向有关。下面假设主轴为从左到右。

flex-start（默认值）：左对齐

flex-end：右对齐

center： 居中

space-between：两端对齐，项目之间的间隔都相等。

space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

#### 3.5 align-items属性

align-items属性定义项目在交叉轴上如何对齐。

.box{align-items:flex-start|flex-end|center|baseline|stretch;}
![](https://liemeday.github.io/blogPic/20201228151010/11.webp)
它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。

flex-start：交叉轴的起点对齐。
flex-end：交叉轴的终点对齐。
center：交叉轴的中点对齐。
baseline: 项目的第一行文字的基线对齐。
stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

#### 3.6 align-content属性

align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
.box{align-content:flex-start|flex-end|center|space-between|space-around|stretch;}
![](https://liemeday.github.io/blogPic/20201228151010/12.webp)
该属性可能取6个值。

flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：轴线占满整个交叉轴。

### 四、项目的属性

以下6个属性设置在项目上。

order
flex-grow
flex-shrink
flex-basis
flex
align-self

#### 4.1 order属性

order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。

.item{order:;}
![](https://liemeday.github.io/blogPic/20201228151010/13.webp)
#### 4.2 flex-grow属性

flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

.item{flex-grow:;/* default 0 */}
![](https://liemeday.github.io/blogPic/20201228151010/14.webp)
如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话）。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。

#### 4.3 flex-shrink属性

flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。

.item{flex-shrink:;/* default 1 */}
![](https://liemeday.github.io/blogPic/20201228151010/15.webp)
如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。

负值对该属性无效。

#### 4.4 flex-basis属性

flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。

.item{flex-basis:|auto;/* default auto */}

它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。

#### 4.5 flex属性

flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。

.item{flex:none|[<'flex-grow'><'flex-shrink'>?||<'flex-basis'>]}

该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。

建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。

#### 4.6 align-self属性

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。

.item{align-self:auto|flex-start|flex-end|center|baseline|stretch;}
![](https://liemeday.github.io/blogPic/20201228151010/16.webp)
该属性可能取6个值，除了auto，其他都与align-items属性完全一致。

## 实例
### 1. flex设置元素垂直居中对齐
HTML代码：
```html
<div class="demo">
 <div class="inner">
  <p>这是一个测试这是一个测试这是一个测试这是一个测试这是一个测试</p>
 </div>
</div>
```

CSS代码：
```css
.demo{
 width: 500px;
 height: 300px;
 border: 1px solid purple;
 display: flex;        /*设置为flex布局*/
 justify-content: center; /*水平居中*/
 align-items: center;  /*垂直居中*/
}

.inner{
 width: 160px;
 height: 160px;
 font-size: 26px;
 border: 1px solid red;
}
```

效果如图：
![](https://liemeday.github.io/blogPic/20201228151010/17.webp)
### 2. 用flex布局制作导航栏

 以前在写导航栏的时候，总是用float或者display：inline-block实现，但是这两种方法都会有各种问题，比如浮动会影响父元素以及兄弟元素的样式，需要清除浮动

 现在用flex会很方便，并且是弹性布局

 HTML代码：
 ``` html
<ul>
<li>音乐</li>
<li>影视</li>
<li>旅游</li>
</ul>
```

CSS代码：
``` css
ul{
 display: flex;    
}

li{
 flex: 1;
 text-align: center;
 line-height: 100px;
}
```

效果如图所示：
![](https://liemeday.github.io/blogPic/20201228151010/18.webp)
我们只要在HTML代码里面多加两个li元素，导航便弹性变化
![](https://liemeday.github.io/blogPic/20201228151010/19.webp)
不需要改变css代码，即可在导航栏中增加项目

### 3. 有时候需要做成左图右文字的样式，如下图所示：
![](https://liemeday.github.io/blogPic/20201228151010/20.webp)
此时用flex会很方便

HTML代码：
```html
<div class="demo">
 <div class="left"></div>
 <div class="right">
   <p>Iphone7 PLUS XXXXXXXXXX</p>
   <span>总人数99</span>
   <span>剩余人数33</span>
   <div class="btn">立即参与</div>
 </div>
</div>
```
CSS代码：
``` css
.demo{

 display: flex;        /*设置为flex布局*/

 justify-content: space-around;

}

.demo > div{

 flex: none;

}

.left{

 width: 200px;

 height: 200px;

 background: #d4cdcd;

}

.right{

 width: 380px;

 height: 200px;

}
```
甚至有多列布局，
![](https://liemeday.github.io/blogPic/20201228151010/21.webp)
HTML代码：
```html
<div class="demo">
 <div class="left"></div>
 <div class="center">
   <p>description</p>
   <p>description</p>
   <p>description</p>
   <span>description</span>
 </div>
 <div class="btn">确认</div>
 <div class="btn">取消</div>
</div>
```
CSS代码：
``` css
.demo{
 width: 600px;
 height: 150px;
 border: 1px solid #b7b2b7;
 margin: 30px auto;
 padding-top: 17px;
 display: flex;        /*设置为flex布局*/
 justify-content: space-around;
}

.demo > div{
 flex: none;
}
```
### 4. 固定百分比布局：

HTML代码：
``` html
<div class="demo">
 <div class="item item1"></div>
 <div class="item item2"></div>
 <div class="item item3"></div>
 <div class="item item4"></div>
</div>
```
 (1) 等分布局：
![](https://liemeday.github.io/blogPic/20201228151010/22.webp)
CSS代码：
```css
.demo{
 display: flex;      
}

.item{
 flex: 1;
}
```
（2）某一个固定
![](https://liemeday.github.io/blogPic/20201228151010/23.webp)

CSS代码：
```css
.demo{
 display: flex;  
}

.item{
 flex: 1;
}

.item2{
 flex: 0 0 50%;
}
```
（3）某两个固定
![](https://liemeday.github.io/blogPic/20201228151010/23.webp)

CSS代码：
```css
.demo{
 display: flex;  
}

.item{
 flex: 1;
}

.item2{
 flex: 0 0 50%;
}

.item4{
 flex: 0 0 20%;
}
```

（4）三个固定
![](https://liemeday.github.io/blogPic/20201228151010/23.webp)
CSS代码：
```css
.demo{
 display: flex;     
}

.item{
 flex: 1;
}

.item1{
 flex: 0 0 10%;
}

.item2{
 flex: 0 0 50%;
}

.item4{
 flex: 0 0 20%;
}
```
### 5. 圣杯布局，如图所示
![](https://liemeday.github.io/blogPic/20201228151010/24.webp)
HTML代码：
```html
<div class="demo">
 <div class="header">头部</div>
 <div class="body">
   <div class="left">left</div>
   <div class="center">center</div>
   <div class="right">right</div>
 </div>
 <div class="footer">底部</div>
</div>
```
CSS代码：
```css
.demo{
 display: flex;
 flex-direction: column;      
}

.demo div{
 flex: 1;
}

.body{
 display: flex; 
}

.header,.footer,.left,.right{
 flex: 0 0 20%!important;
}
```
### 6. 输入框布局，有时需要在输入框的前部添加提示，或者后部添加按钮，如图所示：
![](https://liemeday.github.io/blogPic/20201228151010/25.webp)
HTML代码：
```html
<div class="demo">
 <span class="tip"></span>
 <input type="text" name="" />
 <button>search</button>
</div>
```
CSS代码：
```css
.demo{
 display: flex;
}

input{
 flex:1;
}
```
 ### 7. 底部footer固定在底部，但是不是fixed定位

页面会经常用到固定的底栏，但是当页面内容过少时，footer会到页面中间，下面用flex来解决
![](https://liemeday.github.io/blogPic/20201228151010/26.webp)
HTML代码：
```html
<div class="demo">
 <div class="main">这是主要内容</div>
 <div class="footer">这是底部</div>
</div>
```
CSS代码：
```css
.demo{
  display: flex;
  flex-direction: column;
}

.main{
  flex: 1;
}

.footer{
  width: 100%;
  height: 120px;
}
```
### 8. 流式布局 ，如下如所示：
![](https://liemeday.github.io/blogPic/20201228151010/27.webp)
HTML代码如下：
```html
<div class="demo">
 <div class="item"></div>
 <div class="item"></div>
 <div class="item"></div>
 <div class="item"></div>
</div>
```
CSS代码：
```css
.demo{
  width: 258px;
  height: 300px;
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}

.item{
  flex: 0 0 33.333333%;
  height: 80px;
  box-sizing: border-box;
}
```