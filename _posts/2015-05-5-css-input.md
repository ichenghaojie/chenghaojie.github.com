---
layout: post
title:  以前遇到过，但没重视的input制作按钮在各浏览器之间的兼容性
categories: [css]
author: chenghaojie
excerpt: "css input按钮兼容"
---


* content
{:toc}


网上查了些资料，在这里记录下：

首先是这样一段代码：

    input.item {
    background: #4D90FE;
    border: 1px solid #4D90BB;
    color: white;
    }
    <input type="submit" value="提交" />

这是很简单的一个input提交按钮，它在每个浏览器中的效果都是长短不一，参差不齐的，哪个是标准的也不好说。<br/>
现在我们来对他进行一个修正，修正样式如下：

    .item input {
    background:#4D90FE;
    border:1px solid #4D90BB;
    color:white;
    font-family:Arial,sans-serif,Tahoma; 规定同一字体
    font-size:12px; 规定同一字体大小
    height:25px; 解决Safari和Chrome下的高度问题
    line-height:15px; 协调height，让文字居中
    overflow:visible; 只有设置这个属性IE下padding才能生效
    padding:0 0.5em; chrome、ff默认值；调整其值，让IE和其他浏览器的一致
    width: auto; 现代浏览器下识别
    *width: 1; IE7和IE6识别，设置值为1,我也不知道有何作用，但有些人此处设置值为0
    }
    
后面有注释的六行就是后来添加的。而在chrome下高度”有问题”，不符合我们的预期。

>经测试，firefox下给input设置line-height值是无效的。<br/>
这应该是firefox中已经给input标签的line- height值定死了，那就只有从height和padding入手了。<br/>
经测试，firefox和chrome下，input中padding都有一个默认值padding:0 0.5em;<br/>
当我们将padding调至此默认值时发现IE下的input按钮的高度有了变化。<br/>
再经过height与line-height协调<br/>
这时候input按钮的高度在各大浏览器下都一样了。<br/>