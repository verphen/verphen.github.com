title: Linux下Tomcat开机启动
date: 2015-08-13 20:10:54
categories: linux 
tags:
  - web
  - linux
---
很多时候服务器意外宕机导致tomcat停止，保证服务器启动时tomcat自动重启，做一下配置即可：

	$ vim /etc/rc.d/rc.local 

	追加以下内容即可

		# 设置java环境变量
		export JAVA_HOME=/usr/local/jdk1.8.0_73
		export CLASSPATH=.:$JAVA_HOME/jre/lib/dt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
		export PATH=$PATH:$JAVA_HOME/bin

		# tomcat启动命令
		/usr/local/apache-tomcat-8.0.11/bin/startup.sh
	
	保证文件具有可执行权限
	$ chmod +x rc.local  