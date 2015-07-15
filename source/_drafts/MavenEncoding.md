title: Maven技巧-字符编码
date: 2015-07-15 15:56:00
categories: tools
tags:
  - maven
  - skill
---
在使用maven管理应用开发中，由于团队成员IDE默认打开\新建文件的字符编码不一样，常出现乱码或字符编码错乱问题，在pom.xml的<project>标签内进行以下配置：

	<properties>
		<!-- 文件拷贝时的编码 -->
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<!-- 编译时的编码 -->
		<maven.compiler.encoding>UTF-8</maven.compiler.encoding>
	</properties>

	<project.build.sourceEncoding>默认maven是可识别的,如果不放心,可以再进行如下配置;

	<plugins>
		<plugin>
			<groupId>org.apache.maven.plugins</groupId>
			<artifactId>maven-compiler-plugin</artifactId>
			<version>3.1</version>
			<configuration>
				<source>1.7</source>
				<target>1.7</target>
				<encoding>${project.build.sourceEncoding}</encoding>
			</configuration>
		</plugin>
	</plugins>