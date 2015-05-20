title: Tail command
date: 2015-05-20 16:54:22
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

	$ tail [参数] 文件地址  	# 无参数默认打印文件末尾10行数据

tail命令主要是从指定点（默认末尾10行）开始将文件内容写到标准输出,常用于查看日志文件，具体参数：

	-f : 循环读取(常用于监控应用运行日志)
	-n number: 自定义显示行数

如果number前带正号("+")，则从文件头部第number行开始读取；若带负号（"-"）则从文件尾部倒数number行开始读取; number不指定符号默认为负号,即从尾部倒数number行开始读取内容。

	$ tail -n +5 catalina.out 		# 从catalina.out文件顶部第5行开始读取内容
	
	$ tail -n -5 catalina.out 		# 从catalina.out文件尾部倒数5行开始读取内容

	$ tail -n 5 catalina.out 		# 从catalina.out文件尾部倒数5行开始读取内容

具体参数参考：

	$ man mail		# getting help



