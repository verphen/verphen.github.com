title: MySQL基本使用
tags:
  - mysql
  - command
categories: database
date: 2015-07-08 09:58:06
---

在你使用一项工具的时候，刚开始可能为了进度使用可视化界面来操作，如使用mysql的可视化界面工具mysql-front、navicat等等；在熟悉使用后必须尽量摒弃这些可视化工具来使用原始的命令行，这是内功的修炼；

服务
	service mysql [status|start|stop|restart]	# Debian下mysql当前状态、启动、停止、重启
	service mysqld [status|start|stop|restart]	# RedHat下mysql当前状态、启动、停止、重启
	net [start|stop] mysql 	# windows下启动、停止mysql

用户
	mysql -u username -p*** 	# 登录mysql服务
								# -p和密码之间无空格；避免密码泄露这一步不要输入密码
		-u username 	# 用户名
		-p passwd		# 密码,小写p
		-h host 	# 主机
		-P port		# 端口, 大写P
	mysqladmin -u root -p password ****; 	# 修改root用户密码（该命令在非mysql命令模式下执行）

数据库
	show databases 		# 查看所有数据库列表
	drop database-name 	# 删除数据库
	use database-name 	# 使用数据库database-name
	
表	
	show tables 	# 查看使用数据库的全部表
	describe table-name 	# 显示表属性对象的名称和类型
	drop table-name 	# 删除表
	alter table table-name rename to new-table-name  # 修改表名

存储引擎
	show engines 	# mysql支持的存储引擎
	show table status from databse-name where name = 'table-name' 	# 查看表使用的存储引擎和一些其他信息
	alter table table-name engine = InnerDB  # 修改表table-name的存储引擎为InnerDB





