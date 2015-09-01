title: Linux设置Java环境变量
tags:
  - java
  - linux
categories: java
date: 2015-08-13 19:43:54
---
在Linux下设置设置Java环境变量，下载对应平台的JDK版本；这里有两种格式的jdk版本:

1. rpm 格式
	$ rpm  -ivh  jdk-8u51-linux-x64.rpm

2. tar.gz 格式
	$ tar  -zxvf  dk-8u51-linux-x64.tar.gz  [-C  dist-dir]

设置环境变量

	$ vi /etc/profile

		# profile文件追加下面内容
		export JAVA_HOME= /tools/jdk1.8.0_51
		export PATH=$JAVA_HOME/bin:$PATH
		export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

	$ source /etc/profile	# 使刚设置的环境变量生效

替换 `/tools/jdk1.8.0_51` 为你jdk解压目录；如果配置个人账户的java环境变量只需修改 `vi  ~/.bash_profile`文件即可，后面操作步骤相同；同时，有必要提一下windows下配置环境变量:

	计算机[桌面|资源管理器] -> 属性 -> 高级系统设置 -> 环境变量 -> 系统环境变量 -> 新建Key（存在则追加）

	# 变量名及值"key [value]"
	JAVA_HOME  [E:\tools\jdk1.7.0_55]
	CLASSPATH [.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;]
	Path [%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;]

注意：替换`E:\tools\jdk1.7.0_55`为你jdk的安装目录；若已存在的Path变量值末尾没有分号(;)必须添加分号再追加,或直接将以上的Path值添加在已存在值的最前面.