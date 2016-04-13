---
layout: post
title: js随机排列，可作为打乱数组顺序
categories: [js]
author: chenghaojie
excerpt: "js 数组排序"
---


* content
{:toc}


今天看了一段代码，用js打乱顺序，主要实现图片的随机排列。
>代码如下：

    aData.sort(function (a, b) {return Math.random() > 0.5 ? -1 : 1});
其中aDta是一个数组，这里使用.sort()函数。<br/>
关于sort()函数，在JS中Array对象里内置了一个函数：`arrayobj.sort([sortfunction])`<br/>
这个函数将Array 对象进行适当的排序；在执行过程中并不会创建新的 Array 对象。<br/>
sortFunction方法有两个参数。分别代表每次排序比较时的两个数组项。<br/>
sort()排序时每次比较两个数组项都回执行这个参数，并把两个比较的数组项作为参数传递给这个函数。<br/>
当函数返回值为1的时候就交换两个数组项的顺序，否则就不交换。<br/>
如上例中function(a,b)其中a,b就是要比较的数组中的两个数当返回1时这两个数交换返回-1时不交换。<br/>
如此可以打乱数组顺序，当然也可以升序或降序排列，例如：<br/>
`aData.sort(function (a, b) {return a - b});`此为升序。<br/>
当然也可以这样写：

    function asc(a,b) {
    return a < b ? -1 : 1;//如果a<b不交换，否则交换，即升序排列
    }
