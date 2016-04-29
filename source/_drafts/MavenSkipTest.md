title: Maven 跳过测试
tags:
  - maven
  - command
categories: tools
date: 2016-04-29 14:43:38
---

很多时候，我们需要跳过测试用例来编译程序,你可以使用如下方式进行跳过

## 命令行

	# 不执行测试用例，也不编译测试用例类
	$ mvn install -Dmaven.test.skip=true
	
	亦或

	# 不执行测试用例，但编译测试用例类生成相应的class文件
	$ mvn install -DskipTests

## pom.xml配置

    <plugin>  
        <groupId>org.apache.maven.plugins</groupId>  
        <artifactId>maven-surefire-plugin</artifactId>  
        <version>2.18.1</version>  
        <configuration>  
          <skipTests>true</skipTests>  
        </configuration>  
    </plugin>  
