title: npm 配置
date: 2015-11-24 20:37:54
categories: tools
tags:
  - tools
  - npm
---

设置npm为淘宝镜像:

打开.npmrc文件（在用户主目录下或者nodejs安装目录下）,加入以下配置信息：
	registry = http://registry.npm.taobao.org


$ npm install   	# 根据当前目录的package.json来安装依赖



Windows 系统下设置Nodejs NPM全局路径
	Windows下的Nodejs npm路径是appdata，很不爽，想改回来，但是在cmd下执行以下命令也无效

	npm config set cache "D:\nodejs\node_cache"
	npm config set prefix "D:\nodejs\node_global"

	最后在nodejs的安装目录中找到node_modules\npm\.npmrc（或者用户目录下修改.npmrc）文件

	修改如下即可：

	prefix = D:\nodejs\node
	cache = D:\nodejs\node-cache

	修改之后需要把"D:\nodejs\node"设置到环境变量

