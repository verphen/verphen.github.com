title: Linux命令前后台切换
date: 2016-11-08 21:32:11
categories: linux
tags: [command,linux]
---
注: 命令的前后台切换都是针对当前shell，切换到其他shell无法使用；

$ jobs [option] [number] 		# 查看当前shell后台运行的所有命令或指定命令number作业号
	
	Optons：
		-l 		# 增加显示进程号PID列
		-n		# 显示任务状态变化
		-p		# 仅显示对应的进程号PID
		-r		# 仅显示运行状态（running）的任务
		-s		# 仅显示停止状态（stoped）的任务

	$ ping baidu.com &
	$ ping google.com &
	$ ping youtube.com &
	$ jobs

		[4]   Running                 ping baidu.com &
		[5]-  Running                 ping google.com &
		[6]+  Running                 ping youtube.com &
	
	解读：
		> 中括号中的数字即就是命令所需参数number作业号(非进程号PID)
		> 中括号后面的加号('+')表示最后一个置于后台的命令(作业) 
		> 中括号后面的减号('-')表当前作业之前的一个作业
		> 后台的命令状态类型running(运行)、stopped(停止)、Terminated(结束)

$ <command> &			# 将命令后台运行
$ ctrl + z 				# 挂起程序,将前台正在运行的命令置于后台，并且暂停
$ fg [[%]number] 		# 将最后置于后台(或指定number)的后台命令放在前台(Foreground)运行
$ bg [[%]number] 		# 启动最后(或指定number)的后台(Background)命令
$ kill <%number ...> 	# 停止一个或多个后台命令，多个number用空格隔开
$ ctrl + c 				# 终止前台执行的命令