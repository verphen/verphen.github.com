title: Nginx 安装
date: 2015-11-17 18:08:00
categories: tools
tags:
  - nginx
  - tools
---
安装[nginx](http://nginx.org/)

	$ wget http://nginx.org/download/nginx-1.8.0.tar.gz 	# 下载nginx
	$ tar -zxvf nginx-1.8.0.tar.gz [-C <dir>] 	# 解压[指定目录]
	$ cd nginx-1.8.0
	# 编译nginx
	$ ./configure --prefix=/usr/local/nginx  	# prefix指定安装目录

安装最好出现错误：

		./configure: error: the HTTP rewrite module requires the PCRE library.
		You can either disable the module by using --without-http_rewrite_module
		option, or install the PCRE library into the system, or build the PCRE library
		statically from the source with nginx by using --with-pcre=<path> option.

查看错误日志缺少PCRE library，那安装[PCRE library](http://www.pcre.org/)即可，下载解压：

		$ cd pcre2-{pcre-version}
		$ ./configure
		$ make && make install

安装pcre-devel解决问题
		yum -y install pcre-deve

	重新进去nginx目录

		$ ./configure --prefix=/usr/local/nginx
		$ make && make install 

	http://blog.csdn.net/stuartjing/article/details/6909319
	http://www.cnblogs.com/skynet/p/4146083.html
	http://blog.csdn.net/hfsu0419/article/details/7190152
	

ps:
	
	configure 	# 该文件是软件提供者提供的shell脚本,生成makefilse
	make		# 编译源码，生成Makefile
	make install    # 读取Makefile中的指令，开始安装

	http://nonfu.me/p/4753.html