---
layout: post
title:  Array.prototype.slice.call(arguments)
categories: [js]
author: chenghaojie
excerpt: "js-Array.prototype.slice.call(arguments)分析"
---


* content
{:toc}

首先Array.prototype.slice.call(arguments)能将具有length属性的对象转成数组

    var a={length:2,0:'first',1:'second'};
    Array.prototype.slice.call(a);//  ["first", "second"]

    var a={length:2};
    Array.prototype.slice.call(a);//  [undefined, undefined]
    
Array.prototype.slice.call(arguments)能够将arguments转成数组，等价于arguments.toArray().slice();<br/>
这是用call的例子

    var a = function(){
        console.log(this);    // 'cheng'
        console.log(typeof this);      //  Object
        console.log(this instanceof String);    // true
    }
    a.call('cheng');
    
可以看出，call了后，就把当前函数推入所传参数的作用域中去了<br/>
最后提供个转化成数组的通用函数

    var toArray = function(s){
        try{
            return Array.prototype.slice.call(s);
        } catch(e){
                var arr = [];
                for(var i = 0,len = s.length; i < len; i++){
                    arr.push(s[i]);
                }
                return arr;
        }
    }