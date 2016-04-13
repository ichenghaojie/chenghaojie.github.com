---
layout: post
title: bind()函数在JS面向对象中的作用
categories: [js]
author: chenghaojie
excerpt: "js bind函数"
---


* content
{:toc}


在做面向对象方便的js的编写中，经常会用到自定义的bind()函数：

    bind:function(obj,fn){
        return function(){
            fn.apply(obj,arguments);
        }
    }
主要用于在初始方法中对某个对象绑定事件,一般是这样用的：

    A.prototype={
        initialize:function(obj){
            this._moveDrag = this.bind(this, this.moveDrag);
            this._stopDrag = this.bind(this, this.stopDrag);
            this.addEvent(document, "mousemove", this._moveDrag);
            this.addEvent(document, "mouseup", this._stopDrag);
        },
        moveDrag:function(){

        },
        stopDrag:function(){

        },
        bind:function(obj,fn){
            return function(){
                fn.apply(obj,arguments);
            }
        }
    }
其中bind()主要将this对象限制于上下文的作用域,在添加事件时不受新的作用域的影响。