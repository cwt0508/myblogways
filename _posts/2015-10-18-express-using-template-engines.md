---
layout: post
category: Express
title: express3.x-模板引擎
tags: ['express', '翻译']
author: 张可
email: zhangke@asiainfo.com
description: express3.x中文翻译
---
原文：
<http://expressjs.com/guide/using-template-engines.html>
#在 Express 中使用模板引擎

需要在应用中进行如下设置才能让 Express 渲染模板文件：

·views, 放模板文件的目录，比如： app.set('views', './views')  

·view engine, 模板引擎，比如： app.set('view engine', 'jade')
然后安装相应的模板引擎 npm 软件包。

	$ npm install jade --save 
 

>和 Express 兼容的模板引擎，比如 Jade，通过 res.render() 调用其导出方法__express(filePath,options, callback) 渲染模板。有一些模板引擎不遵循这种约Consolidate.js 能将 Node 中所有流行的模板引擎映射为这种约定，这样就可以和 Express 无缝衔接。


一旦 view engine 设置成功，就不需要显式指定引擎，或者在应用中加载模板引擎模块，Express 已经在内部加载，如下所示。

	app.set('view engine', 'jade');
在 views 目录下生成名为 index.jade 的 Jade 模板文件，内容如下：

	html
	  head
	    title!= title
	  body
	    h1!= message
然后创建一个路由渲染 index.jade 文件。如果没有设置 view engine，您需要指明视图文件的后缀，否则就会遗漏它。

	app.get('/', function (req, res) {
	  res.render('index', { title: 'Hey', message: 'Hello there!'});
	});
此时向主页发送请求，“index.jade” 会被渲染为 HTML。

请阅读 “为 Express 开发模板引擎” 了解模板引擎在 Express 中是如何工作的。
