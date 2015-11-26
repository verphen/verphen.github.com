title: SSH安装
tags:
  - ssh
  - command
categories: linux
date: 2015-06-19 14:17:34
---

检查SSH是否安装(本文采用centos测试)

	$ rpm -qa | grep ssh 	# 只能检查是否通过rpm的软件

如未安装，则安装即可：

	$ yum -y install openssh-server openssh-clients 
	$ service sshd <start|stop|restart> 		# 重启SSH[]
	

<!-- more -->

查看ssh默认端口22是否启动：

	$ netstat -antp | grep sshd 
	或者
	$ iptables -nL 

如端口未打开，那开启防火墙

	$ vi /etc/sysconfig/iptables
	# 插入内容
	-A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT

检查SSH是否为开机启动：
	
	$ chkconfig --list sshd

设置SSH为开机启动：

	$ chkconfig sshd [on|off]    # 开机启动[是|否]

SSH的配置文件：/etc/ssh/sshd_config

	# 限制ip连接
	sshd: <[All|ip]> 	# 指定IP连接[所有|具体IP],当然也可以配置多个IP

远程SSH连接(默认端口22)
	
	$ ssh [-p <port>] <user>@<host>