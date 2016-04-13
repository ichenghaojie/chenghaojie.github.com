---
layout: post
title:  使用CSS3属性box-shadow画图
categories: [css3]
author: chenghaojie
excerpt: "css3 画图"
---


* content
{:toc}


###我们使用box-shadow制作阴影，但也可以利用它来画图。

    box-shadow:inset x-offset y-offset blur-radius spread-radius color
也就是：对象选择器 {box-shadow:投影方式 X轴偏移量 Y轴偏移量 阴影模糊半径 阴影扩展半径 阴影颜色}

>取值：</br>
box-shadow属性至多有6个参数设置，他们分别取值：

>阴影类型</br>
此参数是一个可选值，如果不设值，其默认的投影方式是外阴影；如果取其唯一值“inset”,就是将外阴影变成内阴影，也就是说设置阴影类型为“inset”时，其投影就是内阴影；

>X-offset</br>
是指阴影水平偏移量其值可以是正负值可以取正负值，如果值为正值，则阴影在对象的右边，反之其值为负值时，阴影在对象的左边；

>Y-offset</br>
是指阴影的垂直偏移量，其值也可以是正负值，如果为正值，阴影在对象的底部，反之其值为负值时，阴影在对象的顶部；

>阴影模糊半径：</br>
此参数是可选，，但其值只能是为正值，如果其值为0时，表示阴影不具有模糊效果，其值越大阴影的边缘就越模糊；

>阴影扩展半径</br>
此参数可选，其值可以是正负值，如果值为正，则整个阴影都延展扩大，反之值为负值是，则缩小

>阴影颜色</br>
此参数可选，如果不设定任何颜色时，浏览器会取默认色，但各浏览器默认色不一样，特别是在webkit内核下的safari和chrome浏览器将无色，也就是透明，建议不要省略此参数。

通过：`box-shadow: -2px 0 5px green,0 -2px 5px blue,0 2px 5px red,2px 0 5px yellow;`</br>
分别为上下左右设置阴影。

好基础介绍到这，来说说如何用它画图，代码如下：

    div{
    position: absolute;
    top: 50%;
    left: 50%;
    width: 200px;
    height: 200px;
    margin: 0 auto;
    margin-left: -100px;
    border-radius: 50%;
    box-shadow: 0 0 0 4px rgba(247, 247, 247, 0.53), 0 0 0 200px rgba(177, 30, 30, 0.81), 0 0 0 204px rgba(247, 247, 247, 0.67), 0 0 10px 204px rgba(0, 0, 0, 0.64), 0 0 0 60px rgba(27, 27, 27, 0.79) inset, 0 0 10px 60px rgba(0, 0, 0, 0.73) inset;
    }

为一个div设置一个box-shadow,div,宽度和高度都是200px，</br>
然后前4个box-shadow设置了扩展，并且是向外的这很关键，</br>
而后两个是设置的向内的扩展，并且都是以200x200为基础，</br>
这里要记住当给同一个元素使用多个阴影属性时，需要注意它的顺序，</br>
最先写的阴影将显示在最顶层，所以后面的204看起来只会比前面的200多处4px的扩展。

最后效果图是这样：

<img class="" title="调试页面" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/box-shadow-img.png" alt="" width="500" height="430" />