title: Hexo Blog Error Analysis
date: 2014-12-18 23:47:47
categories: blog
tags: [blog]
---
在使用Hexo生成博客静态文件过程中，出现些许问题；经过google和自己分析总结解决方案如下：

- 中文乱码
- Hexo无法解析模板文件

<!--more-->

<h3>中文乱码</h3>

 answer: 将*.md文件*.yml文件设置成 utf-8；

 新建文章名尽量采用英文命令，防止中文(当然也能处理)带来的不必要的麻烦；我一般采用 "日期+文章名" 的方式命名，如 20140101_articleName.md

<h3>Hexo无法解析模板文件</h3>

 当我们写好文章生成静态文件 `hexo g`进行预览 `hexo s` 出现以下错误:

	<%- partial('_partial/head') %> 
	<%- partial('_partial/header', null, {cache: true}) %>                
	<%- body %>
	<% if (theme.sidebar && theme.sidebar !== 'bottom'){ %> 
	<%- partial('_partial/sidebar'), null, {cache: true} %> <% } %>   
	<%- partial('_partial/footer', null, {cache: true}) %>                
	<%- partial('_partial/mobile-nav', null, {cache: true}) %> 
	<%- partial('_partial/after-footer') %>

如下图：
<img src="http://7xlmfk.com1.z0.glb.clouddn.com/imgs/error/buildHexoBlog1.png" alt="Hexo无法解析模板文件" />

answer: 你博客根目录运行以下命令：
	
	npm install hexo-renderer-ejs --save

    npm install hexo-renderer-stylus --save

    npm install hexo-renderer-marked --save
