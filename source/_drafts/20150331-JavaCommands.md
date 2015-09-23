title: JavaCommands
tags:
---
jps: JavaVirtual Machine Process Status Tool，jdk1.5之后提供的一个查看java进程pid显示的命令

	显示java的进程pid

参数介绍：
	-m : 输出main方法的参数
	-l : 输出完整的包名，应用主类名


	$ java -jar dest.jar 	# 执行目标dest.jar文件
	当然你必须配置jar文件的META-INF下得MANIFEST.MF文件,添加 `Main-Class: cn.effine.MainClass` (MainClass为包含main方法的类)

	