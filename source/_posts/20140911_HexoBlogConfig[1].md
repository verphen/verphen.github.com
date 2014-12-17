title: Hexo Blog Config[1]
date: 2014-09-11 23:22:15
categories: blog
tags: [blog]
---
本文整理简介：

1. 添加导航菜单
2. 长博客显示更多

<!--more-->

- 博客添加Home、Archives同级菜单导航：
	
	- 博客根目录执行命令：`hexo new page pagename` (pagename 是你添加导航菜单的名称,如添加关于about: hexo new page about)，执行完该命令，会在 /source 目录下生产 pagename 文件夹(如about文件夹)，该文件夹下有个 index.md 文件;该文件内容是点击导航菜单显示的页面。<br>
	<img src="/imgs/add_navigation_01.png" alt="directory">
	
	- 修改themes下的_config.yml文件：打开正在使用的 themes 下的 _config.yml 文件， 在 menu 一级菜单下配置菜单显示名称和访问文件路径;依据 Home 导航菜单的配置；如需要显示菜单名"About"，则配置为 `About: /about` ,注意冒号":"后有个空格。
	<br><img src="/imgs/add_navigation_02.png" alt="navigation">
	<br><img src="/imgs/add_navigation_03.png" alt="navigation">

- 针对博客过长，显示主要内容在主页，点击"更多"显示全文
	
	- 在博客简介完成之后添加 ` <!--more-->` 即可<br><img src="/imgs/read_more.png" alt="Read More">
	