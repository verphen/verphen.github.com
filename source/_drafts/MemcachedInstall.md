title: MemcachedInstall
tags:
---
安装memcached之前必须先安装 libevent-devel
	 yum install libevent-devel

安装memcached

	wget http://www.memcached.org/files/memcached-1.4.22.tar.gz
	tar -zxvf memcached-1.x.x.tar.gz
	cd memcached-1.x.x
	./configure && make && make test && sudo make install

测试是否成功安装memcached：
	memcached -h : 是否打印一些memcached信息
		或
 	ls -al /usr/local/bin/mem*

开启memcached守护进程： memcached -d -u root

	#连接参数
		-p 监听端口(默认为11211)
		-l 连接的IP地址,默认是本机
		-d 以守护进程运行
		-u 以什么用户运行(仅以root运行时使用)
		-m 最大内存使用,单位MB,默认64MB,最大2G
		-M 内存耗尽时返回错误
		-c 最大同时连接数量,默认是1024
		-f 块大小增长因子,默认是1.25
		-n 最小分配空间,key+value+flags默认48
		-h 显示帮助

然后确保防火墙已打开正确的端口，在/etc/sysconfig/iptables中添加防火墙规则，打开对应端口
	vi /etc/sysconfig/iptables
	service iptables restart

使用telnet测试memcached是否安装、启动成功
	telnet 124.192.148.18 (telnet <ip|domain name> port)

telnet中的命令：

	quit:退出
	version: 查看版本信息