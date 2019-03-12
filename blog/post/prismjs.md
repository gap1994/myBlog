---
title: 代码美化JS——prismjs
date: 2019-01-07
published: true
tags: ['Markdown', 'prismjs']
series: false
cover_image: ./images/timg.jpg
canonical_url: false
description: "代码美化神器，下载后稍微加个类名就搞定"
---

### 下载
官方下载地址：[http://prismjs.com/](http://prismjs.com/ "http://prismjs.com/")

1. 选择好颜色，我选tomorrow night
2. 选择语言类型
3. 选择插件
4. 点击download下载js和css

### 引用
```
<link rel="stylesheet" href="css/prism.css" />
<script src="js/prism.js"></script>
```
### 使用
```
<pre class="line-numbers"><code class="language-css">p { color: red }</code></pre>
```
### 全代码
```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<link rel="stylesheet" type="text/css" href="css/prism.css" />
	</head>
	<body>
			<pre class="line-numbers">
				<code class="language-css">p { color: red }</code>
			</pre>
		<script src="js/prism.js" type="text/javascript" charset="utf-8"></script>
	</body>
</html>
```


