title: Gradle Commands
tags:
  - gradle
  - commond
categories: algorithm
date: 2016-07-16 20:37:54
---
常用的gradle命令集锦：

    $ gradle        # 欢迎信息
    $ gradle [-v | --version]       # 显示gradle相关版本及相关环境版本信息
    $ gradle eclipse        # 构建eclipse项目开发环境(创建.classpash等文件)
    $ gradle tasks      # 得到可运行的任务和描述的完整列表
    $ gradle assemble       # 编译程序源码打包生成jar文件，不执行单元测试
    $ gradle build      # 编译程序源码打包生成jar文件,执行单元测试
    $ gradle compileJava        # 编译程序中的源代码
    $ gradle clean      # 清理项目构建文件(即就是build文件夹)
    $ gradle test       # 编译
    $ gradle check      # 代码质量检查

使用技巧：
> maven项目秒转成gradle项目:
> 
	$ gradle setupBuild --type pom		# gradle1.7的写法
	$ gradle init --type pom		# gradle2.0的写法

> 设置gradle本地仓库路径：
> 
	设置环境变量即可： GRADLE_USER_HOME = dest-path(目标目录)