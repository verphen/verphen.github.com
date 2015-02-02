title: Redis Install
date: 2015-01-31 23:43:02
categories: redis
tags: [redis,database,tools]
---
周六闲来没事研究点新东西，也满足一个技术宅的好奇心；redis简介google，进入正题：redis(官网： <a href="http://redis.io/">http://redis.io/</a> )环境搭建(centos-minimal)

- redis下载、解压、编译源码
	
		$ wget http://download.redis.io/releases/redis-2.8.19.tar.gz		#下载
		$ tar xzf redis-2.8.19.tar.gz	#解压
		$ cd redis-2.8.19	#进入redis目录
		$ make	#编译

	编译redis源码时可能出现错误："make: cc: Command not found make...",是因为linux没有没有gcc环境(C语言环境), 依照如下步骤安装gcc环境(如已安装跳过)

		$ yum install gcc #安装gcc环境
		$ rpm -qa | grep gcc	#验证gcc是否安装成功（是否打印版本信息）
		$ make  #再次编译redis源码(建议重新解压编译，防止之前生成的无效文件造成编译错误)

<!-- more -->

- 启动redis服务
		
		$ src/redis-server	#前台启动redis服务
		
	如需后台(以daemon守护进程启动)运行redis-server需修改redis.conf下的"daemonize no" 为 "daemonize yes"

	简单尝试redis,另起窗口进入redis-2.8.19,打开redis客户端

		$ src/redis-cli	#redis内置客户端
		127.0.0.1:6379> set foo bar	# 设值：key(foo)-value(bar)
			OK
		127.0.0.1:6379> get foo	#取值：key(foo)
		"bar"

- 总结
	
	如需要将redis的相关命令设置成全局（相当于windows将命令进入环境变量）执行如下命令

		$ make install #将redis-2.8.19/src目录下的redis-*等相关命令复制到/usr/local/bin

	linux执行多条命令小技巧： 多条命令之间可以使用 "&&" 连接, 如 " make && make install " ;
	
	