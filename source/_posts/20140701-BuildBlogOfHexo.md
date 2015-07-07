---
title: Build Blog Of Hexo
date: 2014-07-01 00:50:07
categories: blog
tags: [hexo,github,blog]
---
Hexo是基于nodejs的静态博客生成程序，关于Hexo具体，你可以去google或者参考作者<a href="https://github.com/tommy351">@tommy351</a>对<a href="https://github.com/hexojs/hexo">Hexo</a>的介绍,这里不再累述;

<!-- more -->

<h3>Install Hexo </h3>

安装Hexo之前需要安装nodejs，因为hexo是基于nodejs而生；然后依次按以下步骤进行：

- npm install hexo -g: 安装基于nodejs的hexo modules 

- hexo init blog: 在当前目录创建blog目录作为工作目录，并生成hexo必需文件

<!-- more -->

- cd blog: 进入hexo工作目录   

- npm install: 应该是安装一些node的依赖dependencies

- hexo new "hello hexo": 使用Hexo创建POST，相当于创建一篇博文

- hexo g (hexo generate): 使用hexo生成博客静态文件

- hexo s (hexo server): 启动本地服务(默认启动4000端口),然后在浏览器地址栏输入：`localhost:4000 ` 就可以访问你的博客

针对博客的配置和主题theme的设置参考后面的博客...

具体文档参考：

- <a href="http://hexo.io/">http://hexo.io/</a>
- <a href="https://github.com/hexojs/hexo">https://github.com/hexojs/hexo</a>