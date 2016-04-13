---
layout: post
title:  使用事件源捕获事件,进行对应操作的方法。
categories: [js]
author: chenghaojie
excerpt: "js 事件源捕获"
---


* content
{:toc}


一般使用的是这种模式：

    this.on(oTips, "click", function(event) {
        var oEvent = event || window.event;
        var oTarget = oEvent.target || oEvent.srcElement;
        var i = 0;
        if(oTarget.tagName.toUpperCase() == "A") {
        }
    }
在oTips里面有需要进行点击操作的选项，例如按钮或者一些菜单的点击。<br/>
相比于使用for循环的操作，利用事件源可以更好的在函数外进行操作，<br/>
例如在另外一个函数类使用`oThis.aSort[3].click();`其中`this.aSort[]`是`oTips`里面的元素，<br/>
如果使用的事for循环而不是事件源那就无法操作。