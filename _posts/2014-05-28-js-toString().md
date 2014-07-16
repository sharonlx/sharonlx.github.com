---
layout: post
title:  "Javascript toString() "
date:   2014-05-28
categories: Javascript
---

###toString()

####object.toString()
js中的对象都会从Object.prototype中继承了toString()方法。但是每个对象toString()的行为是有所差异的.

|类型|toString()结果|示例|
|-------|-----|
|Boolean|"true" \| "false"|[示例](http://jsfiddle.net/leexuanr/3HyZd/)
|Number|NaN \| "Number本身"| [示例](http://jsfiddle.net/leexuanr/3HyZd/)
|function|function body|[示例](http://jsfiddle.net/leexuanr/3HyZd/)|
|Object|"[object Object]"|[示例](http://jsfiddle.net/leexuanr/3HyZd/)|
|Date|date日期字符串|var d = new Date();d.toString();|[示例](http://jsfiddle.net/leexuanr/3HyZd/)
|RegExp|RegExp的字符串|[示例](http://jsfiddle.net/leexuanr/3HyZd/)|
|Array|数组元素每个toString()后的结果用","合并|[示例](http://jsfiddle.net/leexuanr/3HyZd/)|
|Error|"Error: message toString()的结果"|new Error(new Boolean(123))// Error: true[示例](http://jsfiddle.net/leexuanr/3HyZd/)|

####Object.prototype.toString()
[\[zz\]参考](http://www.cnblogs.com/ziyunfei/archive/2012/11/05/2754156.html) 
[印象笔记](https://app.yinxiang.com/shard/s9/view/ff1bba19-346f-405e-b4da-4314aba40d53?csrfBusterToken=U%3D1109bf%3AP%3D%2F%3AE%3D146423c56dc%3AS%3D683b19549ddbb726e832927c99a30b2d#st=p&n=ff1bba19-346f-405e-b4da-4314aba40d53)


