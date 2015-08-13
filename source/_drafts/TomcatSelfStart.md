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

	export JAVA_HOME=/home/hostname/jdk1.6.0_31
	export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
	export PATH=$PATH:$JAVA_HOME/bin

	# tomcat启动命令
	/home/install/apache-tomcat-8.0.11/bin/startup.sh