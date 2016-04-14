---
layout: post
title:  ArcGIS for JavaScript marker的添加和删除
categories: [ArcGis]
author: chenghaojie
excerpt: "arcgis 地图的一些基础功能"
---


* content
{:toc}


###先说下情况

1. 最近在与一家软件厂家做地图对接，对方是在ArcGIS地图上做的二次开发，给我的API也是官方的API，我需要在他们地图上实现我们自己公司地图的一些功能（比如目前做的：添加，删除，移动marker等功能），因为只是自己写相关接口，所以我是在官网上下载对应的API和SDK，下面是实现在ArcGIS地图上添加，删除标注的功能。

2. 地图：ArcGIS官方在线地图，ArcGIS Javascript API版本：3.12

软件截图一（在地图上点击后添加的标注标记，点击标注标记后弹出的详细信息）：

<img class="" title="arcgis" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/arcgis-add-marker-1.png" alt="" width="800" height="550" />

主要的函数代码：

<img class="" title="arcgis" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/arcgis-add-marker-2.png" alt="" width="800" height="400" />

