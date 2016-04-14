---
layout: post
title:  js怎么获取xml里某个节点的值
categories: [js]
author: chenghaojie
excerpt: "js xml节点取值"
---


* content
{:toc}


最近在做js编写googleMap接口方面的工作，有些函数接收到的参数是xml，所以需要提取出xml中节点的值。下面看列子：

XML 文件（假设为“names.xml”，注意文件编码）

    <?xml version="1.0" encoding="gbk"?>
    <names>
    <name>张三</name><name>李四</name><name>王五</name>
    </names>
JavaScript 代码（需要放在 HTML 页面中，并在浏览器中执行）

    <script type="text/javascript">
    //---- 加载 XML 文档的函数 ----
    function loadXMLDoc(xmlFile){
        var xmlDoc;
        try{
            //Internet Explorer 可以使用其原生方法加载 XML
            xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
        }catch(e){
            try{
                //Firefox 也有标准方法,但可能造成其他浏览器报错,故省略
                //使用 XMLHttpRequest 替代,适用于大部分浏览器
                var xmlHttp=new XMLHttpRequest() ;
                xmlHttp.open("GET",xmlFile,false) ;
                xmlHttp.send(null) ;
                return xmlHttp.responseXML;
            }catch(e){
                return null;
            }
        }
        xmlDoc.async=false;
        xmlDoc.load(xmlFile);
        return xmlDoc;
    }
    //---- 解析 names.xml 的例子 ----
    var xml=loadXMLDoc("names.xml");
    //获取 XML 文档
    var domElems=xml.getElementsByTagName("name");
    //获取文档中"name"元素节点集合(数组)
    var strNames=new Array(domElems.length);
    //创建"strNames"数组用于存储"用户名"
    for(var i=0;i<domElems.length;i++)
        strNames[i]=domElems[i].childNodes[0].data;
    //取得"name"元素节点的子节点(文本节点)的数据,并存入"strNames"数组
    alert(strNames.join());
    //测试,输出"strNames"数组(预期结果:"张三,李四,王五")
    </script>
    
关键是通过childNodes[0].data取出值

--------------------------------
最后记录下当传来经纬度坐标时，例如：

>lat = 23.14746; lng = 113.34175376;<br/>
要通过：var myLatLng = new google.maps.LatLng(lat, lng);<br/>
转换成地图能够识别的LatLng形式<br/>