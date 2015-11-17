title: "NginxInstall"
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
	$ ./configure 

	出现错误：

		./configure: error: the HTTP rewrite module requires the PCRE library.
		You can either disable the module by using --without-http_rewrite_module
		option, or install the PCRE library into the system, or build the PCRE library
		statically from the source with nginx by using --with-pcre=<path> option.

	分析： 缺少PCRE library

	安装[PCRE library](http://www.pcre.org/), 在官网下载并解压

		$ cd pcre2-{pcre-version}
		$ ./configure
		$ make && make install

	重新进去nginx目录

		$ ./configure
		$ make && make install 

