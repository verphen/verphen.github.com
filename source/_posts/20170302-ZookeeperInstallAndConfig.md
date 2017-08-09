title: Zookeeper 安装及配置
tags: [zookeeper,zk]
categories: tools
date: 2017-03-02 23:33:37
---
Zookeeper（后续简称 zk ） 介绍自行 Google 及参考官网： [http://zookeeper.apache.org][1]；
 
## 一、安装 zk
	# 官网下载对应版本的zk至用户目录（本文实验版本 zookeeper-3.4.9.tar.gz ）
	$ wget http://mirrors.hust.edu.cn/apache/zookeeper/current/zookeeper-3.4.9.tar.gz
	
	$ tar -zxvf zookeeper-3.4.9.tar.gz     # 解压文件
	$ cd zookeeper-3.4.9   # 进入zookeeper根目录
	$ mkdir data logs   # 新建目录data(数据目录)、logs(日志目录)
	$ vi conf/zoo.cfg   # 新建并编辑conf/zoo.cfg文件(zookeeper配置文件，默认不存在，可参考提供的文件 zoo_sample.cfg)
	
	    tickTime=2000
	    dataDir=/${***}/zookeeper-3.4.9/data
	    dataLogDir=/${***}/zookeeper-3.4.9/logs
	    clientPort=2181
	    initLimit=5
	    syncLimit=2

<!-- more -->
## 二、启动 zk
	$ cd zookeeper-3.4.9/bin  # 进入zk命令目录
	$ ./zkServer.sh start  # 启动zk服务
	$ ./zkServer.sh status # 查看zk启动状态(打印信息出现"Mode: standalone"，即表示zk为单点)
	# zk基本基本命令[启动|前台启动|停止|重启|查看状态|升级|打印cmd]
	$ zkServer.sh {start|start-foreground|stop|restart|status|upgrade|print-cmd}

## 三、配置 zk 集群
现提供三台服务器（当然你也可以提供一台机器，使用不同的端口来实现），如下：
	# HostName:  IP
	server1:  10.0.0.21
	server2:  10.0.0.22
	server3:  10.0.0.23
首先，在每台服务器以zk单点形式进行安装，然后分别对zk配置文件 zoo.cfg 添加集群配置：
	# server.[myid]:[ip]:[port1]:[port2]，具体信息参考博文"zoo.cfg配置"
	server.1:10.0.0.21:2888:3888
	server.2:10.0.0.22:2888:3888
	server.3:10.0.0.23:2888:3888
其次，在每台服务器zk的配置目录conf下新建 myid 文件,同时将上一步配置的“myid”值写入对应服务器myid文件即可；如 10.0.0.21 配置的myid文件内容为“1”，后面两台类推；具体操作： 
	# 将myid为"1"写入server1的myid文件 
	$ echo "1" > ~/zookeeper-3.4.9/conf/myid 
	 
	# 将myid为"2"写入server2的myid文件
	$ echo "2" > ~/zookeeper-3.4.9/conf/myid
	
	# 将myid为"3"写入server3的myid文件
	$ echo "3" > ~/zookeeper-3.4.9/conf/myid
最后，分别启动或重启zk即完成集群配置，zk会自动选举leader及follower（目前的配置会是1台为leader、两台为follower，使用`zkServer.sh status`查看状态）  







[1]:	http://zookeeper.apache.org