---
layout: post
title:  js获取对象数组的属性(key)和值(value)
categories: [js]
author: chenghaojie
excerpt: "js获取键值对的通用方法"
---


* content
{:toc}


今天遇到了这样一种情况，先贴图:

<img class="" title="arcgis" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/js-array-value.png" alt="" width="210" height="140" />

由图可以看到在一个`{}`中,存放了一个对象`2:[]`,因为有可能下次这个`{}`中会存入`1:[]`,所以我不能通过`object[2]`,这种方法去取其中的数组，而此时这个数组就是这个对象对应的value,所以我们通过一个通用方法去取的了它的值。

    function getObjectKeys(object)
    {
        var keys = [];
        for (var property in object)
        keys.push(property);
        return keys;
    }

    function getObjectValues(object)
    {
        var values = [];
        for (var property in object)
        values.push(object[property]);
        return values;
    }
    
对于上面的表述可能存在问题，所以我贴出了标准的方法。