---
layout: post
title:  node.js 代码覆盖测试
categories: [node.js]
author: chenghaojie
excerpt: "node.js 使用mocha进行代码覆盖测试"
---


* content
{:toc}


首先呢，我们需要安装`istanbul`，这个跟`mocha`结合起来非常不错
>cnpm install –save istanbul

怎么使用呢？就是直接就是
istanbul cover main.js

<img class="" title="node.js" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/nodejs-debug-1.png" alt="" width="640" height="220" />

这里显示的statements（表达式）、branches(分支)、function（函数）的意思。

接下来就是结合 istanbul 和mocha，实现代码的全面测试
在命令行中输入:
istanbul cover _mocha

但出错了。

<img class="" title="node.js" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/nodejs-debug-2.png" alt="" width="640" height="420" />

怎么回事呢，其实我也是遇到这个问题的时候也是一头雾水的，到处找资料，</br>
后来说是那个mocha版本跟istanbu版本有很大的依赖性，</br>
所以正确的方式就是安装mocha到项目目录中，然后使用项目里面的mocha进行测试，使用如下命令：
>istanbul cover node_modules/mocha/bin/_mocha

就可以看到我们想看的结果了

<img class="" title="node.js" src="https://raw.githubusercontent.com/ichenghaojie/ichenghaojie.github.io/master/images/nodejs-debug-3.png" alt="" width="640" height="360" />