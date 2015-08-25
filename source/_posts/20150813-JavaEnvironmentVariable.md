title: Linux设置Java环境变量
tags:
  - java
  - linux
categories: java
date: 2015-08-13 19:43:54
---
在Linux下设置设置Java环境变量，下载对应平台的JDK版本；这里有两种格式的jdk版本:

1. rpm 格式
	$ rpm -ivh jdk-8u51-linux-x64.rpm

2. tar.gz 格式
	$ tar -zxvf dk-8u51-linux-x64.tar.gz [-C dist-dir]

设置环境变量

	$ vi /etc/profile

		# profile文件追加下面内容
		export JAVA_HOME= /tools/jdk1.8.0_51
		export PATH=$JAVA_HOME/bin:$PATH
		export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

	$ source /etc/profile	# 使刚设置的环境变量生效 

随便提一下windows下配置环境变量

	计算机[桌面|资源管理器] -> 属性 -> 高级系统设置 -> 环境变量 -> 系统环境变量 -> 新建（存在则追加）

	# 变量名及值"key [value]"
	JAVA_HOME  [E:\tools\jdk1.7.0_55]
	CLASSPATH [.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;]
	Path [%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;]