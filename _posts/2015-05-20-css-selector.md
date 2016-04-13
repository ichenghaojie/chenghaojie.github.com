---
layout: post
title:  对CSS :first-child 选择器误解
categories: [css]
author: chenghaojie
excerpt: "css 选择器"
---


* content
{:toc}


记录下自己对CSS :first-child 选择器误解。

首先是CSS :first-child 选择器的正确用法：

引用w3school的例子：

>p:first-child i（这段代码指的是选择`<p>` 中的每个 `<i>` 元素并设置其样式，
其中的 `<p>` 元素是其父元素的第一个子元素，如果`<p>`元素不是父元素的第一个子元素，
那`<i>`元素的样式将无法匹配。）

>li:first-child （这段代码指的是`<li>`元素父元素下的第一个`<li>`， 同时`<li>`也必须是第一个子元素，否则样式无法匹配） 

>ul>:first-child（这段代码指的是为每个 `<ul>` 的首个子元素设置其样式）

>ul>li:first-child（不同于上一个例子，这里指为`<ul>`下的第一个li设置样式， 同时`<li>`也必须是第一个子元素，否则无法设置样式）