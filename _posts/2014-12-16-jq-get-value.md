---
layout: post
title: 关于JQ取父元素的值以及自定义序列化字符串以符合json格式
categories: [jq]
author: chenghaojie
excerpt: "jq问题"
---


* content
{:toc}


    var input=$j("[name=items]:checkbox");//取得name为items的checkbox

    var data="";

    for(var i=0;i&lt;input.length;i++){

    if(data.length&gt;0){data+=","} //添加","做分隔

    if(input[i].checked){

       data+="\""+input[i].value+"\":["+"\""+$j(input[i]).parent().next().html()+"\""+",\""+$j(input[i]).parent().next().next().html()+"\"]";

    }
    
当要查找input[i]的父元素时，要用$j(input[i]).parent()，input[i]要包裹$j(),然后可以用html()取出数据.