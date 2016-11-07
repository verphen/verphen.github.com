title: ChkconfigCommands
tags:
---

有时我们需将某些服务做成开机启动，然后把服务做成shell脚本(参考博文ChkconfigShellTemplate)放在目录/etc/rc.d/init.d，先前的做法是在/etc/rc.d/目录的rc0.d-rc6.d文件夹分布创建shell脚本的软链接，而现在直接使用chkconfig命令即可实现(chkconfig --add filename).

chkconfig命令主要用来更新（启动或停止）和查询系统服务的运行级信息。谨记chkconfig不是立即自动禁止或激活一个服务，它只是简单的改变了符号连接。


基本语法：

usage:   chkconfig [--list] [--type <type>] [name] 		# 列出当前服务的启动信息
         chkconfig --add <name>			# 添加一个服务由chkconfig管理
         chkconfig --del <name>			# chkconfig管理服务列表移除服务
         chkconfig --override <name>
         chkconfig [--level <levels>] [--type <type>] <name> <on|off|reset|resetpriorities>		# 改变服务的状态

Options:
	name 		# 服务名
	type
	level		# 系统运行级别（范围为0-7）




