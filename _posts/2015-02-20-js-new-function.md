---
layout: post
title: 关于new functionName()
categories: [js]
author: chenghaojie
excerpt: "js new关键词"
---


* content
{:toc}


今天调一段程序，发现:

    window.onload=function(){
        new autoPlay("box");
    }
如果缺少了new这个关键词，就会报错，提示`this.play is not a function`<br/>
程序大致是这样的：

    var autoPlay=function(id){this.play(id)};
    autoPlay.prototype={
    play:function(id){}
    }
    window.onload=function(){
    new autoPlay("box");
    }
然后到处查了下其他博客。<br/>

下面摘至：[对new functionName()的理解 ](http://blog.csdn.net/stalwartwill/article/details/26451461；)<br/>
>比如定义一个函数的两种调用方法：

    function getInfo() {
        var info = {
        message: "message"
        };
        return info;
    }
1.var info1 = getInfo();

2.var info2 = new getInfo();

1和2有什么区别吗？info1和info2得到的值是一样的吗？

>第1种很简单，用的也很多，就是执行一个函数，并接受函数的返回值并赋给info1对象；

>第2种情况一般就很少见了。<br/>
首先，函数也是一种对象，是对象肯定就可以实例化（实例化其实就是调用对象的构造函数对对象进行初始化），<br/>
所以第2种情况就是调用getInfo函数对象的构造函数，并接收构造函数初始化的实例（一般都是this），<br/>
而函数有个比较特别的地方就是，如果构造函数有显示返回值，将用该返回值替换this对象返回。<br/>
所以第2中情况new getInfo就是调用构造函数（函数的构造函数就是其定义本身）并接收返回值info。<br/>
所以我这里是通过new autoPlay("box");也就是调用autoPlay函数的构造函数。<br/>
深入说的话就会扯到new FunctionName()的内部机制。
推荐看这篇文章：[从一个实例，看new FunctionName()的内部机制](http://www.cnblogs.com/youxin/p/3355968.html)。<br/>
这里也说到为什么上面的代码是：

    var autoPlay=function(id){this.play(id)};
    autoPlay.prototype={
        play:function(id){}
    }
>而不推荐：

    var autoPlay=function(id){
        this.play(id);
        autoPlay.prototype={
            play:function(id){}
        }
    };