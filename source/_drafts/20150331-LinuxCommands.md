title: LinuxCommands
tags:
---

man command / command --help 可以查看命令command的帮助文档

lsblk 列出块设备。除了RAM外，以标准的树状输出格式，整齐地显示块设备

md5sum filename 检验文件是否被改变

dd 复制或转换文件，可以用来制作usb启动器; dd if=/home/centos.iso of=/dev/sdb1 bs=512M; sync (可以使用lsblk查看usb所在块的名称)

uname： unix name；显示机器名

	-a: 查看操作系统和内核的详细信息 
		Linux YLJYLVS1 2.6.32-431.el6.x86_64 #1 SMP Fri Nov 22 03:15:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
		Linux - 机器内核名
		YLJYLVS1 - 机器的节点名
		2.6.32-431.el6.x86_64 - 内核发布的版本
		#1 SMP - 内核版本
		x86_64 - 处理器架构
		GNU/Linux - 操作系统名

history : 操作系统终端执行过的命令历史
	 
		按住“CTRL + R”就可以搜索已经执行过的命令，它可以在你写命令时自动补全。

		如：(reverse-i-search)`if': ifconfig 
















