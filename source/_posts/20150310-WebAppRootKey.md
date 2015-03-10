title: web.xml配置WebAppRootKey
date: 2015-03-10 17:47:34
categories: java
tags: [web.xml]
---
容器 Tomcat 运行多个web项目(测试时运行student、teacher两个web项目)，发生如下错误：

	Web app root system property already set to different value: 'webapp.root' = 
	[/home/user/tomcat/webapps/student/] 
	instead of [/home/user/tomcat/webapps/teacher/] - Choose unique values for the 'webAppRootKey' 
	context-param in your web.xml files!  

	--------------------------------------------------
		方便页面展示，错误经过合理的换行处理
	--------------------------------------------------

错误提示指出： key为` "webapp.root" `已经指向项目student, 不能在指向项目teacher


出现原因: tomcat 容器下的web项目的 web.xml 都没有配置或配置相同的 WebAppRootKey;
