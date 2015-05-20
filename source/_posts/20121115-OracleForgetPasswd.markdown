---
title: 忘记oracle sys/system/scott用户密码解决方案
date: 2012-11-15 01:33:12
categories: database
tags: [oracle,数据库]
---
1. 忘记除SYS、SYSTEM用户之外的用户的登录密码。

	用SYS (或SYSTEM)用户登录: CONN SYS/PASS_WORD AS SYSDBA;
	
	使用如下语句修改用户的密码: ALTER USER user_name IDENTIFIED BY newpass;
	
	注意：密码不能全是数字。并且不能是数字开头。否则会出现：ORA-00988: 口令缺失或无效

2. 忘记SYS用户，或者是SYSTEM用户的密码。

	如果是忘记SYSTEM用户的密码，可以用SYS用户登录。然后用ALTER USER 密令修改密码：
	
	CONN SYS/PASS_WORD AS SYSDBA;
	
	ALTER USER SYSTEM IDENTIFIED BY newpass;
	
	
	如果是忘记SYS用户的密码，可以用SYSTEM用户登录。然后用ALTER USER 密令修改密码。
	
	CONN SYSTEM/PASS_WORD ;
	
	ALTER USER SYSTEM IDENTIFIED BY newpass;

3. 如果SYS,SYSTEM用户的密码都忘记或是丢失。

	这一项尤其重要。
	
	可以使用ORAPWD.EXE 工具修改密码。
	
	开始菜单->运行->输入‘CMD’,打开命令提示符窗口，输入如下命令：
	
	orapwd file=D:\oracle\product\10.2.0\db_1\database\pwdctcsys.ora password=newpass


	这个命令重新生成了数据库的密码文件。密码文件的位置在ORACLE_HOME目录下的\database目录下。

	这个密码是修改sys用户的密码。除sys和system其他用户的密码不会改变.