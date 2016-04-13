---
layout: post
title: 获取页面中偏移量的方法
categories: [js]
author: chenghaojie
excerpt: "js 获取页面偏移量"
---


* content
{:toc}


今天看到一个获取在页面中偏移量的函数：

    var getOffset = {
        top: function (obj) {
            return obj.offsetTop + (obj.offsetParent ? arguments.callee(obj.offsetParent) : 0)
        },
        left: function (obj) {
            return obj.offsetLeft + (obj.offsetParent ? arguments.callee(obj.offsetParent) : 0)
        }
    };
另外一种写法：

    function getPos(obj) {
        var iTop = obj.offsetTop;
        var iLeft = obj.offsetLeft;
        while (obj.offsetParent)
        {
            iTop += obj.offsetParent.offsetTop;
            iLeft += obj.offsetParent.offsetLeft;
            obj = obj.offsetParent;
        }
        return {top:iTop, left:iLeft}
    };
>一开始没看懂，仔细想想才理解到：*这是递归，一层一层往上累加offsetTop，元素的偏移量是根据它的直接父元素来定义的。*</br>
所以利用这个方法得到的是obj相对于整个浏览器页面的top，left。</br>
又回顾了下其它资料，记录下：</br>
client=padding+content,不包含滚动条的宽高　(而offset=padding+content+border+scroll，也就是offset=client+border+scroll) ,</br>
重点：client就是两部分组成的，padding和content;offset由四部分组成，不含margin。</br>
所以无论谁在算width或height时都不用理会margin。</br>