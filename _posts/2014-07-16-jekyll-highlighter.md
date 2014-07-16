---
layout: post
title:  "让jekyll支持语法高亮"
date:   2014-07-16
categories: jekyll
---
###让jekyll支持语法高亮

参考

* [syntax-highlighting-with-pygments-is-failing-via-liquid-templates-string-error](http://stackoverflow.com/questions/7801197/syntax-highlighting-with-pygments-is-failing-via-liquid-templates-string-error)
* [syntax-highlighting-markdown-code-blocks-in-jekyll-without-using-liquid-tags](http://stackoverflow.com/questions/8648390/syntax-highlighting-markdown-code-blocks-in-jekyll-without-using-liquid-tags)
* [832-rolling-out-the-redcarpet](https://github.com/blog/832-rolling-out-the-redcarpet)

本身呢jekyll是支持语法高亮的，只需要在*_config.yml* 中设置 *highlighter: pygments* 就可以了，但是这样做呢，你的代码部分必须这样写

	{% highlight bash %}
	cd ~
	{% endhighlight %}

因为jekyll默认使用liquid 标签来做语法高亮。但是这样做的好处是，markdown中签入了liquid标签，这样markdown文件就不独立了，作为一个程序员这个是无法忍受的。如果你能忍受，那么跳过下面的文字吧。

目前有三种解决方案：

#####一、将jekyll的模板解析切换为*redcarpet* 

1. 首先在本地环境中安装*redcarpet*
	
		[sudo] gem install redcarpet
		
2. 然后在*_config.yml*文件中添加 *markdown\: redcarpet* 修改markdown的解析器
3. 写文章时，遇到代码，就可以按照下面的规范写

		```bash
		cd ~
		```
4. 语法高亮还需要一个语法高亮样式，可以自行去下载一个，我目前用的是[语法高亮样式](https://raw.githubusercontent.com/mojombo/tpw/master/css/syntax.css) 但是这个样式对于js支持不太好。

按照上面的配置就可以对markdown中的代码进行语法高亮了。
		
可以看到这样做的好处是markdown本身并没有引入其他标签，保持文章的独立性，坏处是你需要去下载redcarpet的，并且确保你的博客本身是支持*redcarpet*的

遗憾的是我现在还没找到到底extentions的全部列表

#####二、使用插件的形式

1. 从github上下载插件[Jekyll-plugins](https://github.com/nono/Jekyll-plugins) 
2. 在你的*project* 目录下新建文件夹*_plugins*
3. 将插件放到*_plugins*目录中，然后修改*_config.yml*文件


	```ruby
	markdown: redcarpet2
	redcarpet:
  	extensions: ["no_intra_emphasis", "fenced_code_blocks", "autolink", "strikethrough", "superscript", "with_toc_data"]
	 ```
	 
#####三、使用hightlighter.js 来进行语法高亮

因为github pages 是可以用使用js的，所以可以通过下载highlighter.js来渲染

如果你的博客系统是支持redcarpet的，那么最好用第一种方法。