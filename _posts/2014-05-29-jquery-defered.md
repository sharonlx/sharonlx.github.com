---
layout: post
title:  "jQuery的Defered对象"
date:   2014-05-29
categories: Defered jQuery
---

###[翻译]jQuery的Defered对象简介

由于Jquery的Defered是基于CommonJS的Promise/A，所以先简单介绍一下Promise

####CommonJS Promise/A
[原文地址](http://wiki.commonjs.org/wiki/Promises/A)

#####提案
Promise是CommonJS提出的规范。一个邀约(promise)有三种状态unfulfiled,fulflled 和 failed。邀约只能从unfulfilled到fulfilled或者从unfulfilled到failed。这样可以避免其他负面影响，比如死循环调用。

Promise对象有一个then的方法属性，then的定义如下

		then(fulfilledHandler, errorHandler, progressHandler)

当promise对象被填充完后会调用*fulfilledHandler*,如果Promise对象failed，那么会触发*errorHandler*方法。其中这三个参数是可选择，并且如果不可选必须是*function*类型的参数，否则会被忽略。

当fulfilledHandler或者errorHandler回调函数完成后，then方法必须返回一个新的填充好的promise对象，这样才能实现promise的链式调用。从回调函数返回的值，将是then方法最终返回的promise对象的填充值，如果回调函数有异常，那么promise对象的状态将被设置为failed.

		asyncComputeTheAnswerToEverything().then(addTwo).then(printResult, onError);// 44
		
一个可交互的promise对象，必须是可拓展的，所以应该支持下面几种方法：

		get(properName);//获取promise对象中属性为properName的值，该方法返回一个promise对象
		call(functionName, arg1, arg2);//调用functionName的方法，并且讲this设置为当前的promise对象

####Defered API介绍