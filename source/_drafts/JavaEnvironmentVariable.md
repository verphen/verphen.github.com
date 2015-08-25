title: Java设置环境变量
date: 2015-08-13 19:43:54
categories: java 
tags:
  - java
  - 总结
---
在Linux下设置设置Java环境变量，下载对应平台的JDK版本；这里有两种格式的jdk版本(我使用的版本jdk-8u51-linux-x64)：

1. rpm格式
	
	$ rpm -ivh jdk-8u51-linux-x64.rpm

2. tar.gz格式

	$ tar -zxvf dk-8u51-linux-x64.tar.gz

设置环境变量
	
	1. 所有用户可用
		$ vi /etc/profile

			export JAVA_HOME= /home/yunlu/install/jdk1.8.0_51
			export PATH=$JAVA_HOME/bin:$PATH
			export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

		$ source /etc/profile

	2. 针对指定用户
		$ vi ~/.bash_profile

			export JAVA_HOME= /home/yunlu/install/jdk1.8.0_51
			export PATH=$JAVA_HOME/bin:$PATH
			export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

		$ source /etc/profile

顺便提一下windows下配置环境变量

	计算机[桌面|资源管理器] -> 属性 -> 高级系统设置 -> 环境变量 -> 系统环境变量 -> 新建 

	JAVA_HOME -- E:\jdk1.7.0_55
	CLASSPATH -- .;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;
	Path -- %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;