title: Maven技巧-下载源码
date: 2015-07-15 11:42:19
categories: tools
tags:
  - maven
  - skill
---
通过maven下载依赖文件的源码和JavaDoc，便于我们学习和借鉴

1. maven命令行(针对具体项目)

	mvn dependency:sources 	# 下载依赖文件源码
	mvn dependency:resolve -Dclassifier=javadoc 	# 下载依赖文件JavaDoc

2. 配置maven全局文件settings

	在配置文件<profiles> 标签内加入以下配置：

	<profile>    
		<id>downloadSources</id>    
		<properties>         
			<downloadSources>true</downloadSources>         
			<downloadJavadocs>true</downloadJavadocs>               
		</properties> 
	</profile> 

<!-- more -->

	然后在标签 <settings> 内加入配置：

	<activeProfiles>
		<activeProfile>downloadSources</activeProfile>
	</activeProfiles>

	标签<activeProfiles>默认在<settings>的最后，默认为注释状态

3. eclipse配置

	操作步骤： window -> Preferences -> Maven
	在右边出现的多选项中，勾选"Download Artifact Sources"（源码） 及"Download Artifact JavaDoc"(JavaDoc)即可