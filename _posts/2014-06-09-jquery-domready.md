---
layout: post
title:  "Javascript domReady"
date:   2014-06-09
categories: Javascript jQuery
---

### domready详解
参考
[JS、CSS以及img对DOMContentLoaded事件的影响](http://www.alloyteam.com/2014/03/effect-js-css-and-img-event-of-domcontentloaded/)、[从onload和DOMContentLoaded谈起](http://www.cnblogs.com/hh54188/archive/2013/03/01/2939426.html)


* #### DOMContentLoaded 和 onload

很多框架都自带时间domready,然后其他初始化的逻辑都放在这个事件的回调函数中。在说这个事件之前，我们先来说说*document* 的 *DOMContentLoaded* 和 *window* 的*onload*两个事件

\*\*PS: onload方法是所有具有src属性的标签公有的事件，比如*img*、*script*、*window*、*iframe*、*embed*

\*\*PS: *document.readyState* 有如下几种状态：

状态 |描述 | 其他
------------ | ------------- | ------------
uninitialized| XML对象被产生，但是没有任何文件被加载|暂无法出现|
loading| 加载其他资源，但是文档尚未开始解析| DOMContentLoaded事件触发之前文档的状态|
interactive|除了image、flash、或者子frame这些资源未加载意外，其他资源都请求，并且标签已经全部解析好|DOMContentLoaded事件触发后，onload事件触发前|
completed|文档的全部资源已经加载完毕|window.onload事件触发后|


*DOMContentLoaded* 事件默认情况下，不会等待样式表、图片和子页面的加载，而是当外链脚本全部执行完毕后就触发*DOMContentLoaded*时间。此时*document*对象的*readyState*值为*interactive*。


\*\*PS:但是当script标签前有link标签来外链一个样式表时，无论实在head中还是body中，都会阻塞当前script的执行，script脚本会等待样式表加载完毕后再执行。

\*\*PS:浏览器会同时请求css和js，但是会等到css加载完毕后在执行js

\*\*PS:火狐浏览器即使script写在link标签前，也会先加载样式，然后再执行script

当页面的所有资源都加载完毕后，会触发*window.onlaod*事件， 此时*document*对象的*readyState*值为*completed*

* #### jQuery的dom ready

首先根据*document.readyState*判断，是否为*completed*

对非IE浏览器，挂载*DOMContentLoaded* 和 降级处理的 *load* 事件。

对于IE浏览器，由于有些属性，是必须在DOM解析完毕后才具有的，例如*doScroll*所以可以轮训的判断改属性是否已有值