title: "MySQL基本使用"
date: 2015-07-08 09:58:06
categories: database
tags:
  - mysql
  - command
---
在你使用一项工具的时候，刚开始可能为了进度使用可视化界面来操作，如使用mysql的可视化界面工具mysql-front、navicat等等；在熟悉使用后必须尽量摒弃这些可视化工具来使用原始的命令行，这是内功的修炼；

	service mysql [status|start|stop|restart]	# Debian下mysql当前状态、启动、停止、重启
	service mysqld [status|start|stop|restart]	# RedHat下mysql当前状态、启动、停止、重启
	net [start|stop] mysql 	# windows下启动、停止mysql

	mysql -u username -p 	# 登录mysql服务
		-u username 	# 用户名
		-p passwd		# 密码,小写p
		-h host 	# 主机
		-P port		# 端口, 大写P

	show databases 		# 查看所有数据库
	drop database-name 	# 删除数据库
	use database-name 	# 使用数据库database-name
	show tables 	# 查看使用数据库的全部表
	describe table-name 	# 显示表属性对象的名称和类型
	drop table-name 	# 删除表




