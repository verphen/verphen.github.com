title: LinuxCommands
tags:
---

echo $variable-name   打印环境变量名的值

![command]  	# 执行最近执行过的命令command

netstat -tln | grep 8080 查看端口8080的使用情况

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

sudo : super user do; 允许授权用户执行超级用户或者其它用户的命令;sudo允许用户借用超级用户的权限，然而"su"命令实际上是允许用户以超级用户登录。所以sudo比su更安全

mkdir : make direactory;创建目录
rmdir  删除文件夹

touch：命令代表了将文件的访问和修改时间更新为当前时间。touch命令只会在文件不存在的时候才会创建它。如果文件已经存在了，它会更新时间戳
rm 	删除文件或文件夹

chmod: 命令就是改变文件的模式位。chmod会根据要求的模式来改变每个所给的文件，文件夹，脚本等等的文件模式（权限）。在文件(文件夹或者其它，为了简单起见，我们就使用文件)中存在3中类型的权限
	Read(r): 4
	Write(w): 2
	Execute(x): 1

apt: Advanced package Tool ;APT是一个为Debian系列系统（Ubuntu，Kubuntu等等）开发的高级包管理器，在Gnu/Linux系统上，它会为包自动地，智能地搜索，安装，升级以及解决依赖

	apt-get / apt-cache 的使用

	-------- ubuntu安装及卸载软件-----------
	- 安装：apt-get install xxx
	- 卸载：apt-get remove xxx
	- 更新：apt-get upgrade xx

	apt-get install docker.io  安装docker
     apt-get remove - - purse docker.io



cal: Calender 日历

date: 查看时间；这个命令在脚本中十分有用，以及基于时间和日期的脚本更完美

cat: concatenation连结;连接两个或者更多文本文件或者以标准输出形式打印文件的内容
	“>>”和“>”调用了追加符号。它们用来追加到文件里，而不是显示在标准输出上。“>”符号会删除已存在的文件，然后创建一个新的文件。所以因为安全的原因，建议使用“>>”，它会写入到文件中，而不是覆盖或者删除

		* 零个或更多字符
		？ 恰好一个字符
		[abcd] 恰好在列举范围中的一个字符
		[a-z] 恰好在所给范围中的一个字符
		[!abcd] 任何字符都不在列举范围内
		[!a-z] 任何字符都不在所给范围内
		{debain,centos}  恰好在所给选项中的一个单词

    - 查看文件内容：cat filename
    - 新建文件：cat > filename (输入初始文本内容，按回车，ctrl+D <发送EOF: end of file>退出；如     果该目录存在文件filename则覆盖)
    - 将一个或多个文件内容复制进另外的文件：cat filename1 filename2 >> filename3（">"新建，">>"追加）显示文件内容


cp: 复制

mv: 移动或更名

cd     进目录（".."上一级目录；"~"home目录;"-"上次进入的目录）
pwd     打印当前目录
ls     显示当前目录文件和文件夹


kill: 杀死进程

ps: 管道
	- ps：查看后台进程（常用"ps aux"）
    - a  显示其他用户启用的进程
    - u  启动这个现场的用户和它启用的时间
    - x  查看系统中属于自己的进程
    - ps -ef | grep java (查看与java有关的线程)
    ps axe | grep docker 查看docker进程
	ps aux

	

grep: 匹配

cd: change directory; 改变目录

free -m: 查看内存使用情况

wget: 下载文件

grep: Global Regular Expression Print 全局正则表达式版本
	$ grep "search content"  "dest file" 搜索目标文件指定内容

	$ who -r 	# 查看服务器允许级别(同命令runlevel)
	$ find /home -mtime +120 	# 在/home目录下找出120天之前被修改过的文件
	$ find /usr -size +10M 	# 在/usr目录下找出大小超过10MB的文件
	$ find /var \! -atime -90	# 在/var目录下找出90天之内未被访问过的文件
	$ find / -name core -exec rm {} \; 	# 在整个目录树下查找文件“core”，如发现则无需提示直接删除它们
	find  查找文件(默认末尾加命令"-print"用于显示)

配置ip及网络配置文件：

	$ vi /etc/sysconfig/network-scripts/ifcfg-eth0

配置防火墙(端口)文件

	$ vi /etc/sysconfig/iptables
	修改完成如需立即生效，执行
	$ service iptables restart

技巧：

	终端保持当前目录不变，去别的目录执行命令；只需把要执行的命令加上括号即可;

	$ clear 	# 清屏(同操作ctrl + l)