---
layout: post
title:  "移动页面开发之微信篇"
date:   2014-07-23
categories: mobile
---
###移动页面开发之微信篇


####微信分享好友、朋友圈、腾讯微博

iOS版的微信，一旦点击页面中的链接进行过跳转，即使点击返回回到最初页面，*window.location* 却不是最初页面的url，而是跳转后链接的url。这样如果你点击微信自带的分享功能，那么分享出去的链接地址是跳转后的链接地址。

Android版本的微信不会有这种问题。

修复的方法是在页面中添加下面的代码。

#####监听微信分享好友事件

```js

	// 发送给好友

    WeixinJSBridge.on('menu:share:appmessage', function (argv) {
        // alert('发送给好友');

        WeixinJSBridge.invoke('sendAppMessage', { 

            'img_url': shareData.imgUrl,

            'img_width': shareData.imgWidth,

            'img_height': shareData.imgHeight,

            'link': shareData.sendFriendLink,

            'desc': shareData.fContent,

            'title': shareData.fTitle

        }, function (res) {
            // alert(res.err_msg);
            
        });

    });
        
```

点击微信分享时 微信的浏览器会触发*menu:share:appmessage* 事件

 * *img_url* 	微信分享中的图片地址
 * *img_width*	微信分享中的图片宽度
 * *img_height*	微信分享中的图片高度
 * *link*		微信分享的链接地址
 * *desc*		微信分享的描述
 * *title*		微信分享的标题
 
##### 监听微信分享到朋友圈
 
```js
	WeixinJSBridge.on('menu:share:timeline', function (argv) {

        WeixinJSBridge.invoke('shareTimeline', {

            'img_url': shareData.imgUrl,

            'img_width': shareData.imgWidth,

            'img_height': shareData.imgHeight,

            'link': shareData.timeLineLink,

            'desc': shareData.tContent,

            'title': shareData.tTitle

        }, function (res) {

             // alert('timeline', res.err_msg);

        });

    });
 ```
 		
 点击分享到朋友圈时，微信的浏览器会触发*menu:share:timeline* 事件
 
##### 监听微信分享到腾讯微博
 
```js
WeixinJSBridge.on('menu:share:weibo', function (argv) {

    WeixinJSBridge.invoke('shareWeibo', {

        'content': shareData.wContent,

        'url': shareData.weiboLink

    }, function (res) {

        // alert('weibo', res.err_msg);

    });

});
```
 点击分享到腾讯微博，微信浏览器会触发 事件

```js

document.addEventListener('WeixinJSBridgeReady', function onBridgeReady() {


   /*监听分享到好友*/
   
   /*监听分享到朋友圈*/
   
   /*监听分享到微博*/   
    
}, false);
```

        