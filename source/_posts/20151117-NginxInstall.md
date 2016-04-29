title: linux安装nginx
tags:
  - nginx
  - tools
categories: tools
date: 2015-11-17 18:08:00
---

若你的项目需要用到负载均衡、反向代理、静态文件服务器等功能，那你需赶快入手nginx，她能超轻量级的完成你所需功能；现我们开始第一步安装 nginx： [http://nginx.org/](http://nginx.org/) （以下讲解环境使用centos，其他环境安装方式大同小异）

	$ wget http://nginx.org/download/nginx-1.8.0.tar.gz 	# 下载相应版本nginx
	$ tar -zxvf nginx-1.8.0.tar.gz [-C <dir>] 	# 解压[指定目录]
	$ cd nginx-1.8.0
	$ ./configure --prefix=/usr/local/nginx  	# prefix指定安装目录

<!-- more -->

安装过程出现的错误解析：
	
	# 错误 1
	checking for C compiler ... not found
	./configure: error: C compiler cc is not found

分析/解决：不存在C编译环境，安装即可：yum install gcc (如果不存在C++编译环境，使用命令安装即可: yum install gcc++)

	# 错误 2
	./configure: error: the HTTP gzip module requires the zlib library.
	You can either disable the module by using --without-http_gzip_module
	option, or install the zlib library into the system, or build the zlib library
	statically from the source with nginx by using --with-zlib=<path> option.

分析/解决：不存在zlib library；安装即可：yum install -y zlib-devel

	# 错误 3
	./configure: error: the HTTP rewrite module requires the PCRE library.
	You can either disable the module by using --without-http_rewrite_module
	option, or install the PCRE library into the system, or build the PCRE library
	statically from the source with nginx by using --with-pcre=<path> option.

分析/解决：缺少PCRE library; 那下载源码安装[PCRE library](http://www.pcre.org/)即可(注意下载的是prce而不是prce2)，下载解压安装：

	$ cd pcre-{version}
	$ ./configure
	$ make && make install

当然你也可以使用命令： yum install pcre

	# 错误 4
	./configure: error: the HTTP cache module requires md5 functions
	from OpenSSL library.   You can either disable the module by using
	--without-http-cache option, or install the OpenSSL library into the system,
	or build the OpenSSL library statically from the source with nginx by using
	--with-http_ssl_module --with-openssl=<path> options.

分析/解决： 缺少OpenSSL library; 安装：yum install openssl openssl-devel 

    # 错误5
    nginx: [emerg] bind() to 0.0.0.0:9000 failed (48: Address already in use)
   
解决：地址(端口)已经被使用，修改端口重新加载nginx（nginx -s reload）;有可能是需要root用户启动，可以尝试

    # 错误6
    nginx: [emerg] open() "/usr/local/nginx/logs/nginx.pid" failed (13: Permission denied)

解决： 没有权限，使用root用户启动

根据nginx源码安装延伸
	. configure 	# 该文件是软件提供者提供的shell脚本,生成makefilse
	. make		# 编译源码，生成Makefile
	. make install    # 读取Makefile中的指令，开始安装

若文章阐述有误，欢迎指正；我会及时修正，以误他人！