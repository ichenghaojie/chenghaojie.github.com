---
layout: post
title:  js变量提升的问题
categories: [js]
author: chenghaojie
excerpt: "看js面试题时遇到的，基础知识"
---


* content
{:toc}


直接看例子：

例子一：

<img class="" title="变量提升" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/js- variables-improve-1.png" alt="" width="200" height="150" />

结果是 10.<br/>
这是因为在函数bar内，foo被变量提升，在函数开始首先var foo,此时foo为undefined，所以会进入if，进行赋值。

例子二:

<img class="" title="变量提升" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/js- variables-improve-2.png" alt="" width="200" height="150" />

结果是1.我们先不分析，先看下例子三。

例子三：

<img class="" title="变量提升" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/js- variables-improve-3.png" alt="" width="200" height="150" />

结果却是10.<br/>
例子二和例子三有什么差别呢？<br/>
例子二中进行了变量提升，在函数内重新var a,然后函数内的变量是局部变量，不会影响到全局变量，所以全局变量a的值还是1。(其实对于这点我还是不清楚，所以只是这样理解，如果有错误请留言指出，谢谢。)<br/>
而例子三中并没有进行变量提升，而只是进行了赋值操作，此时的a是全局变量中的a，所以结果会是10.