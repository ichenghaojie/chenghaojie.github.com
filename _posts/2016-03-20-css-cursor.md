---
layout: post
title:  cursor:url();在IE下鼠标样式没有改变
categories: [css]
author: chenghaojie
excerpt: "css cursor的坑"
---


* content
{:toc}


解决这个BUG花了将近两个小时，又是百度又是找美工做图，后来终于在一个评论里找到了问题的所在，居然是**IE识别路径不一样**！！！

使用cursor:url(xxx.cur)时,**ie是相对于页面的路径,而chrome是相对于css文件路径**(假设是在.css独立文件里面).

还有就是各浏览器间鼠标图片大小不一致问题：这种问题应该和各浏览器间对Cursor图片的解析有关系，起初美工给了我鼠标图片，格式是cur的所以我不知道大小，但在ie8及以下图片变大了，后来让美工把鼠标图片的尺寸改为32x32后，图片大小不一致的问题就解决了。
(经测试发现，超过**32x32**尺寸，就会出现这种问题)