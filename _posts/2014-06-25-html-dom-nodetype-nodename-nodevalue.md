---
layout: post
title:  "nodeType和nodeValue "
date:   2014-06-25
categories: Html
---

### HTML DOM 节点的nodeType nodeName nodeValue

[代码](http://jsfiddle.net/leexuanr/w5XwH/5/)

 * nodeName 属性含有某个节点的名称
 
节点类型| nodeName值 | 示例
------ | --------- | ------------
元素节点| 元素的标签名称 | DIV
属性节点| 属性的名称 | 
文本节点| #text | 
注释节点| #comment|
文档节点| #document| DOCUMENT


 * nodeValue 

节点类型| nodeValue值 | 示例
------ | --------- | ------------
元素节点| null | 
属性节点| 属性的值 | name
文本节点| 节点包含的文本 | 我是李璇
注释节点| 注释的内容|
文档节点| null| 


 * nodeType
 
节点类型| nodeType值 | 示例
------| --------- | ------------
元素节点| 1| div
属性节点| 2 | name
文本节点| 3|
注释节点| 8| 我是李璇
文档节点| 9| 
