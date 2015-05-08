title: Rsync Command
date: 2015-05-08 14:27:12
categories: linux
tags:
  - linux
  - rsync
---
rsync - remote synchronized 远程同步工具；采用增量压缩方式进行同步，提高了文件同步的效率。

以下采用centos进行讲解，其他平台原理相同，自行参考研究

既然设计文件的远程同步，需要两台服务器s1\s2

环境描述：
	
	centos 

	serverA: 192.168.0.140 待同步的服务器（源服务器）
	serverB: 192.168.0.141 同步到的服务器 (目标服务器)

	需求: 同步serverA的 /home/test 目录到 serverB 的相同目录（/home/test）

1. 安装rsync

	。 源码安装（安装之前保证本机安装gcc）
		rsync官网（http://rsync.samba.org/） #下载最新发行版本，目前最新版本rsync-3.1.1.tar.gz；
		$ tar -zxvf rsync-3.1.1.tar.gz    #解压
		$ cd rsync-3.1.1 进入rsync目录
		$ ./configure --prefix=/usr  ;make ;make install  

	。 软件包安装

		$ yum install rsync

2. 配置rsync

	默认rsync需要配置三个文件rsyncd.conf \ rsyncd.secrets \ rsyncd.motd; 如文件不存在则创建即可

	rsyncd.conf: 主配置文件，主要配置rsync同步信息和权限设置;默认可能该文件不存在，需手动创建。

	$ vi /etc/rsyncd.conf   #创建rsyncd.conf文件并在vi中编辑

	具体内容参考我的配置

		#Global Settings
		pid file = /var/run/rsyncd.pid
		port = 873
		address = 192.168.0.140

		#以什么身份运行rsync
		uid = root
		gid = root

		use chroot = false
		read only = no

		#limit access to private LANs
		hosts allow = 192.168.0.141
		hosts deny=*
		max connections = 5 
		motd file = /etc/rsyncd.motd

		[backup]
		path = /home/test
		list=yes 
		auth users = rsync
		secrets file = /etc/rsyncd.secrets 
		coment = welcome backup !
		log file = /var/log/rsyncd.log
		lock file = /var/run/rsyncd.lock

	auth users属性可以添加多个用户，用户之间用逗号分隔；所有的用户必须为服务器真实存在的用户

	rsyncd.secrets： 存放用户密码文件,格式"用户名：密码"

	$ vi /etc/rsyncd.secrets   

	参考我的配置

		# username:passwd
		rsync:test123

	$chown root.root rsyncd.secrets 　#修改属主
	$ chmod 600 /etc/rsyncd.secrets   #将rsyncd.secrets这个密码文件的文件属性设为root拥有, 且权限要设为600, 否则无法备份成功!

	
	rsyncd.motd : 存放rsync服务器信息,客户端连接成功显示的信息,无格式限制; 此文件不是必须，若不配置则注释掉rsync.conf中的motd file属性

	$ vi /etc/rsyncd.motd 


3. 开启rsync端口873(开启防火墙)

	$ vi /etc/sysconfig/iptables

	添加如下Code
	
	#-A INPUT -m state --state NEW -m udp -p udp --dport 873 -j ACCEPT
	-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 873 -j ACCEPT

