title: MySQL基本使用
tags:
  - mysql
  - command
categories: database
date: 2015-07-08 09:58:06
---

在你使用一项工具或技术的时候，刚开始可能为了进度使用可视化界面来操作，如使用mysql的可视化界面工具mysql-front、navicat等等学习mysql一样；在熟悉使用后必须尽量摒弃这些可视化工具来使用原始的命令行，这是内功的修炼；

- 服务 service
		service mysql [status|start|stop|restart]	# Debian下mysql当前状态、启动、停止、重启
		service mysqld [status|start|stop|restart]	# RedHat下mysql当前状态、启动、停止、重启
		net [start|stop] mysql 	# windows下启动、停止mysql

- mysql
		mysql>  \s 		# 查看mysql的版本信息和字符编码
		mysql>  show variables;     # 查看mysql的变量设置，可以使用like过滤
		mysql>  show variables like 'autocommit';     # 查看mysql事务是否自动提交
		mysql>  set name utf8;    # 设置字符编码(告诉mysql用utf8编码来处理客户端传过来的sql)

<!-- more -->

- 用户 user
		# 登录mysql服务,-p和密码之间无空格；避免密码泄露这一步不要输入密码
		mysql -u username -p***；
			-u username 	# 用户名
			-p password 	# 密码,小写p
			-h host 		# 主机
			-P port 		# 端口, 大写P

Tag: 针对用户的操作即就是操作数据库默认mysql.user表，你可以使用一般操作表的sql语句操作用户;如更新用户密码:
		
		# 更新用户 test1 的密码为“123456”
		mysql>  update mysql.user set password=password('123456') where User='test1' and Host='localhost';
		# 将更新内容重新加入内存
		mysql>  flush privileges;

针对mysql.user表的操作最后都必须执行 `flush privileges;`,将执行的更新信息重新加入到内存；
	
		# 用户的操作都在mysql数据库的user表
		mysql>  create user username[@host] [identified by 'password']；
			username 	# 待创建的用户名
			host 		# 用户操作的主机,默认为'%'表示可以操作任意主机
			password 	# 用户密码；不设置表示密码为空，用户登录mysql不需要密码验证

		# 删除用户,不指定主机host参数表示 usernmae@'%'
		mysql>  drop user username[@host]；

		# 修改root用户密码（该命令在非mysql命令模式下执行）
		mysqladmin -u root -p password ****； 	

		# 给用户授权
		mysql>  grant privileges on databaseName.tableName to username@host；
				privileges 	# 权限名;全部权限为all，多个权限使用逗号分隔

		# 赋予用户"给其他用户授权"权限
		mysql>  grant privileges on databaseName.tableName to username@host with grant option;

		# 查看用户已有权限
		mysql>  show grants for username[@host]；	

		# 撤销用户权限
		mysql>  revoke privileges on databaseName.tableName from username@host；

		# 创建只读用户（对指定主机的所有数据库）
		mysql>  grant select on *.*  to username[@host] identified by 'passowrd'；

		# 查看当前登录用户和主机
		mysql>  select user();

- 数据库 database
		mysql>  create database database-name； 	# 创建数据库
		mysql>  show databases；					# 查看所有数据库列表
		mysql>  drop database database-name;	# 删除数据库
		mysql>  use database-name； 				# 使用数据库database-name

- 表	 table
		mysql>  show tables ；	# 查看使用数据库的全部表
		mysql>  describe[desc] table-name； 	# 显示表属性对象的名称和类型
		mysql>  drop table-name； 	# 删除表
		mysql>  alter table table-name rename to new-table-name；  # 修改表名
		mysql>  alter table table-name drop fild-name；  # 删除表字段file-name
		mysql>  alter table table-name modify fild-name type-name； 	# 修改字段数据类型
		mysql>  alter table table-name change old-fild new-fild type-name； 	# 修改字段名称和数据类型

- 存储引擎 engine
		# mysql支持的存储引擎
		mysql>  show engines；
		# 查看表使用的存储引擎和一些其他信息
		mysql>  show table status from databse-name where name = 'table-name'；
		# 修改表table-name的存储引擎为InnerDB
		mysql>  alter table table-name engine = InnerDB；

- 方法、函数 function
		# 将查询结果field字段名用指定分隔符（默认为逗号）分隔显示
		group_concat([distinct] field [order by asc/desc order_field] [sepatator '分隔符'])	

- 技巧

	sql语句最后的分号";"替换为"\G"则可以改变查询结果的显示方式,便于用户查看;
