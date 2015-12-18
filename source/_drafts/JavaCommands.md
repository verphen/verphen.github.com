title: JavaCommands
tags:
---

	$ jps 	# JavaVirtual Machine Process Status Tool，jdk1.5之后提供的一个查看java进程pid显示命令
		-m 		# 输出main方法的参数
		-l 		# 输出完整的包名，应用主类名

	$ java -jar dest.jar 	# 执行具有main方法的dest.jar
	
		配置jar的META-INF下得MANIFEST.MF文件指定包含main方法的类(如`Main-Class: cn.effine.MainClass`)

	$ javap -c className		# jdk自带的反编译命令




	java javac jps ,jstat ,jmap, jstack