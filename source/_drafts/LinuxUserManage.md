title: Linux 用户管理
tags: linux
---

	1. su uername; 切换用户
	2. who; 显示所有登录用户
	3. useradd; 添加用户
	4. passwd user;修改用户密码


	1. 添加用户 useradd username（adduser username  ,会默认创建用户环境 ）
	2. 修改密码：passwd username

用户列表文件：/etc/passwd
用户组列表文件：/etc/group
查看系统中有哪些用户：cut -d : -f 1 /etc/passwd
查看可以登录系统的用户：cat /etc/passwd | grep -v /sbin/nologin | cut -d : -f 1
查看用户操作：w命令(需要root权限)
查看某一用户：w 用户名
查看登录用户：who
查看用户登录历史记录：last
