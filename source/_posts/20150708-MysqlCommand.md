title: MySQL基本使用
tags:
  - mysql
  - command
categories: database
date: 2015-07-08 09:58:06
---

在你使用一项工具的时候，刚开始可能为了进度使用可视化界面来操作，如使用mysql的可视化界面工具mysql-front、navicat等等；在熟悉使用后必须尽量摒弃这些可视化工具来使用原始的命令行，这是内功的修炼；

- 服务 service

	service mysql [status|start|stop|restart]	# Debian下mysql当前状态、启动、停止、重启
	service mysqld [status|start|stop|restart]	# RedHat下mysql当前状态、启动、停止、重启
	net [start|stop] mysql 	# windows下启动、停止mysql

- mysql

	\s 		# 查看mysql的版本信息和字符编码
	show variables;     # 查看mysql的变量设置，可以使用like过滤
	show variables like 'autocommit'     # 查看mysql事务是否自动提交
	set name utf8     # 设置字符编码(告诉mysql用utf8编码来处理客户端传过来的sql)

<!-- more -->

- 用户 user

	mysql -u username -p*** 	# 登录mysql服务
								# -p和密码之间无空格；避免密码泄露这一步不要输入密码
		-u username 	# 用户名
		-p passwd		# 密码,小写p
		-h host 	# 主机
		-P port		# 端口, 大写P

	Tag: 针对用户的操作即就是操作数据库默认mysql.user表，你可以使用一般操作表的sql语句操作用户;如更新用户密码:
		`update mysql.user set password=password('123456') where User='test1' and Host='localhost';`
		`flush privileges;`
		针对mysql.user表的操作最后都必须执行 `flush privileges;`,将执行的更新信息重新加入到内存；
	
	create user username[@host] [identified by 'password'] 	# 用户的操作都在mysql数据库的user表
		username 	# 待创建的用户名
		host 	# 用户操作的主机,默认为'%'表示可以操作任意主机
		password 	# 用户密码；不设置表示密码为空，用户登录mysql不需要密码验证
	drop user username[@host] 	# 删除用户,不指定主机host参数表示 usernmae@'%'
	mysqladmin -u root -p password ****; 	# 修改root用户密码（该命令在非mysql命令模式下执行）

	grant privileges on databaseName.tableName to username@host 	# 给用户授权
		privileges 	# 权限名;全部权限为all，多个权限使用逗号分隔
	grant privileges on databaseName.tableName to username@host with grant option; 	# 赋予用户"给其他用户授权"权限
	show grants for effine[@host] 	# 查看用户已有权限
	revoke privileges on databaseName.tableName from username@host 	# 撤销用户权限

	grant select on *.*  to username[@host] identified by 'passowrd'  # 创建只读用户（对指定主机的所有数据库）

	select user(); 	# 查看当前登录用户和主机

- 数据库 database
	
	create database database-name 	# 创建数据库
	show databases 		# 查看所有数据库列表
	drop database-name 	# 删除数据库
	use database-name 	# 使用数据库database-name

- 表	 table

	show tables 	# 查看使用数据库的全部表
	describe[desc] table-name 	# 显示表属性对象的名称和类型
	drop table-name 	# 删除表
	alter table table-name rename to new-table-name  # 修改表名
	alter table table-name drop fild-name  # 删除表字段file-name
	alter table table-name modify fild-name type-name 	# 修改字段数据类型
	alter table table-name change old-fild new-fild type-name 	# 修改字段名称和数据类型

- 存储引擎 emgine

	show engines 	# mysql支持的存储引擎
	show table status from databse-name where name = 'table-name' 	# 查看表使用的存储引擎和一些其他信息
	alter table table-name engine = InnerDB  # 修改表table-name的存储引擎为InnerDB

- 技巧
	
	sql语句最后的分号";"替换为"\G"则可以改变查询结果的显示方式,便于用户查看;
