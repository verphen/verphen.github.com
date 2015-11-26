---
title: Nodejs 安装
date: 2014-06-30 01:42:14
categories: web 
tags: [nodejs,windows,ubuntu]
---

nodejs听说过一段时间了，最近因为想使用hexo搭建自己的博客需要使用到nodejs，特此整理了一下对其的安装。

Windows安装

1. 官网下载：[http://nodejs.org/](http://nodejs.org/) ，两种安装方式：
	-   exe 安装：下载对应平台的exe文件，将下载的node.exe文件复制到需要安装的目录，且将该目录加入到系统环境变量path；（建议采用，熟悉原理）
	-   msi 安装：包装exe安装方式，自动设置环境变量及复制node.exe到C:\program file目录
	
	测试是否安装成功：
		
		$ node <[-v|--version]>        # 显示版本信息
	
<!-- more -->

2. 安装npm (Node Package Manager)
	
	现在的node最新版本已经默认集成npm，所以不需要额外安装; 若是以前较低版本参考如下安装：
	
		$ npm -v         # 测试npm是否安装（如打印版本信息说明已安装）
		# Git自行查询安装
		$ git config --system http.sslcainfo /bin/curl-ca-bundle.crt
		$ git clone --recursive git://github.com/isaacs/npm.git                   # git克隆npm项目到本地
		$ cd npm
		$ node cli.js install npm -gf
 
3. 安装过程中错误分析

	- 出现 `npm ERR! registry error parsing json` 错误，可能需要设置npm代理,执行命令 `npm config set registry http://registry.cnpmjs.org`