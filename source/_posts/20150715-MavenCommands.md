title: Maven 命令详解
tags:
  - maven
  - command
categories: tools
date: 2015-07-15 10:43:38
---

用了maven很多年，针对常用的命令做个总结，方便查阅

    $ mvn archetype:create	# 创建 maven 项目

    #maven生成web项目
    $ mvn archetype:create -DgroupId='package-name' 
      -DartifactId='projectname' -DarchetypeArtifactId=maven-archetype-webapp

    # maven生成java项目
    $ mvn archetype:create  -DgroupId=package-name  -DartifactId=project-name  

    $ mvn compile     # 编译源码
    $ mvn test-compile    # 编译测试源码
    $ mvn test        # 运行应用的单元测试
    $ mvn clean   # 清理项目编译文件

<!-- more -->

    $ mvn package     # 打包（mvn -Dtest package     只打包不测试）
    $ mvn clean package -Dmaven.test.skip=true  # 跳过编译测试程序打包项目
    $ mvn jar:jar     # 打包成jar文件
    $ mvn install     # 本地Repository仓库中安装项目jar文件
                    #（mvn install -D maven.test.skip=true 跳过TestCase检验，否则在install时会运行TestCase测试）
    $ mvn site    # 生成项目相关网站信息(/target/site)
    $ mvn validate    # 验证工程是否正确，所需要的资源是否可用
    $ mvn deploy      # 发布项目

    $ mvn dependency:sources      # 下载依赖包的源码
    $ mvn dependency:resolve -Dclassifier=javadoc     # 下载依赖包的javadoc

    # 启动服务前需执行mvn package及配置相应插件
    $ mvn jetty:run   # 启动jetty服务
    $ mvn tomcat:run  # 启动tomcat服务

    $ mvn eclipse:eclipse     # 生成eclipse项目文件,将项目转换成eclipse项目
    $ mvn eclipse:clean       # 清理eclipse项目文件
    $ mvn idea:idea       # 生成idea项目文件,将项目转换成idea项目
    $ mvn idea:clean      # 清理idea项目文件