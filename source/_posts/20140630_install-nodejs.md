---
title: 安装NodeJS
date: 2014-06-30 01:42:14
categories: web 
tags: [nodejs,windows,ubuntu]
---
node.js听说过一段时间了，最近因为想使用hexo搭建自己的博客需要使用到node.js，特此整理一下node.js的安装。

### Windows安装node.js
1. 官网下载：[http://nodejs.org/download/](http://nodejs.org/download/ "下载node.js") ，两种安装方式：
	- exe 安装：下载对应平台的exe文件，将下载的node.exe文件复制到需要安装的目录，且将该目录加入到系统环境变量path；（建议采用，熟悉原理）
	- msi 安装：包装exe安装方式，自动设置环境变量及复制node.exe到C:\program file目录
	
	测试是否安装成功：` node --version ` 显示版本信息

2. 安装npm
	
	记得有人说npm相对于nodejs,就相当于maven相对于java，不知道这种比拟是否恰当，暂且这么理解

	- 安装npm之前需要安装git（具体安装参考google）
	- 执行命令`git config --system http.sslcainfo /bin/curl-ca-bundle.crt`（说实话我也不知道这个命令什么意思）
	- 克隆npm仓库到本地`git clone --recursive git://github.com/isaacs/npm.git myblog`，克隆npm仓库到当前目录下的myblog文件夹；
	- 进入myblog目录 `cd myblog` ；执行命令`node cli.js install npm -gf` （命令含义无从而知），
	- 测试是否成功执行命令`npm install -d` ,如果在最后出现信息`npm info ok`则说明成功安装npm

3. 安装过程中错误分析

	- 出现 `npm ERR! registry error parsing json` 错误，可能需要设置npm代理,执行命令 `npm config set registry http://registry.cnpmjs.org`
	
### ubuntu安装node.js  （待续）

