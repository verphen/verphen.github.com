title: MysqlCommands
tags:
---

启动与停止mysql服务： net start/stop mysql

连接mysql：mysql -h localhost -u root -p aichuan (-h:主机；-u:用户名；-p:密码)

		   mysql-hlocalhost -uroot -p;回车；要求你输入密码


show databases: 显示所有数据库

use database_name : 使用数据库

show tables: 显示数据库所有表

修改密码：
	SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpass');
	或
	update user set password=password('root') where user ='root';
	flush privileges;

创建用户：
	 insert into mysql.user(Host,User,Password) values("localhost","test",password("1234"));

<Context path="" docBase="/yunlu-admin"  reloadable="false" source="org.eclipse.jst.jee.server:yunlu-admin"/>

select * from t1 left join t2 on t1.id = t2.id 
如果on的时候两个表字段名相同，可以用using关键字
select * from t1 left join t2 using(id)


http://blog.chinaunix.net/uid-26706281-id-3075372.html