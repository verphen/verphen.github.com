title: Tail Command
date: 2015-04-08 22:12:22
categories: linux
tags:
  - linux
  - command
---
<img src="/imgs/linux/tail.png" alt="tail command" />

每次部署项目上线后，通过tomcat的日志文件catalina.out监控项目的运行情况.

	$ tail -f <tomcat-dir>/logs/catalina.out   	# 屏幕即不断追加打印tomcat的运行日志

当然，强制关闭打印屏幕 ctrl + c 即可. 

<!--  more  -->

tail 命令基本用法：

	$ tail [参数] [文件地址]		# 基本用法

tail命令主要是从指定点开始将文件内容写到标准输出（屏幕）
