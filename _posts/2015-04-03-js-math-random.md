---
layout: post
title:  javascript--Math.random方法--返回随机数
categories: [js]
author: chenghaojie
excerpt: "js Math.random方法"
---


* content
{:toc}


Math.random()方法返回介于0 到1 之间一个随机数，不包括0 和1。<br/>
如果想大于这个范围的话，可以套用一下公式：<br/>
>值= Math.floor(Math.random() * 总数+ 第一个值)

>alert(Math.floor(Math.random() * 10 + 1)); //随机产生1-10 之间的任意数

    for (var i = 0; i<10;i ++) {
        document.write(Math.floor(Math.random() * 10 + 5)); //5-14 之间的任意数
        document.write('<br />');
    }
为了更加方便的传递想要范围，可以写成例如下面这个返回随机颜色的函数：

    randomRange: function(lower, upper) {
        return Math.floor(Math.random() * (upper - lower + 1) + lower);
    },
    getRanColor: function() {
        var str = this.randomRange(0, 0xFFFFFF).toString(16);
        while(str.length < 6) str = "0" + str;
        return "#" + str;
    }