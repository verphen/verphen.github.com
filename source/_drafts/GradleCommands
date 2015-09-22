title: Gradle Commands
date: 2015-09-16 20:37:54
categories: algorithm
tags:
  - gradle
  - tools
---
gradle: 欢迎信息
gradle -v: 显示gradle相关版本	

创建一个空目录，依照Maven规范创建项目目录
	
	$ vi build.gradle 	# 创建文件并编辑

	  `apply plugin: 'java'`

	gradle tasks: 可运行的任务和描述列表
	gradle build: 构建项目
	gradle clean: 清理项目(删除构建项目)
	gradle assemble: 该任务编译程序中的源代码，并打包生成Jar文件，这个任务不执行单元测试
	gradle compileJava: 编译程序中的源代码
	gradle test: 编译


技巧： build.gradle文件的注释和Java注释语法一样;

	// 单行注释

	/*
	* 多行注释
	*/

	/**
	* 多行注释
	*/

	maven项目秒转成gradle项目:

		$ gradle setupBuild --type pom		# gradle1.7的写法
		$ gradle init --type pom		# gradle2.0的写法

	设置gradle本地仓库路径：

		设置环境变量即可： GRADLE_USER_HOME = dest-path(目标目录)