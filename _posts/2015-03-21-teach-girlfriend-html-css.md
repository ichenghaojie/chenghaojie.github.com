---
layout: post
title:  转载-js中for in 和 for each in的用法和区别
date:   2014-12-06 15:14:55
categories:[js]
author: chenghaojie
excerpt: "js for 循环"
---

* content
{:toc}


本文将谈谈javascript 中for in 和 for each in的用法和区别

区别一：

    for in是javascript 1.0 中发布的。
    for each in是作为E4X标准的一部分在javascript 1.6中发布的，而它不是ECMAScript标准的一部分。
    这将意味着存在各种浏览器的兼容性问题。for each in，对很多浏览器都不支持的。例如是不支持IE6，IE7，IE8等浏览器的。

区别二：

    var 长方形= { 高:"15", 宽:"25" };

    for (var i in 长方形){
    alert( i + "，" + 长方形[i] );
    }
结果依次是： 高，15 ； 宽，25 ；

    for each (var i in 长方形){
    alert( i + "，" + 长方形[i] );
    }
结果依次是： 15， undefined ； 25， undefined；

两种遍历方法的变量i的值是不一样的，for each in无法获得对象的属性名，只能获取到属性值。

最后总结一下使用建议：

1. 遍历普通数组，建议使用原生的遍历方法for，不要贪图方便，因为for in 和for each in均存在浏览器的兼容问题，不能保证它们对数组的遍历顺序（如果对顺序的不作要求的话，可以使用for in ，但本人不建议），有兴趣话，可以阅读的下一篇文章《for in 的浏览器兼容问题》。

2. 遍历对象，由于for没办法提供理想的遍历，因而只能选择其他方法。这里建议使用for in ，从上面讲解的区别，for in比for each 更具优势，for in能获取索引和属性值，而for each只能获取属性值，而且for each在很多低版本的浏览器是不支持。

如要转载，请注明出处 -- 网海聚焦（WEB攻城狮）