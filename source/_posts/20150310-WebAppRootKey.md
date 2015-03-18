title: web.xml配置WebAppRootKey
tags: [web,java]
categories: java
date: 2015-03-10 17:47:34
---
Web应用服务器 Tomcat 同时运行多个web项目，必须在每个项目的web.xml的 <web-app> 内进行如下配置：
	
	<web-app>
	<context-param>
		<param-name>webAppRootKey</param-name>
		<param-value>webapp.root</param-value>  <!-- 更改"webapp.root"为自定义的任意字符串 -->
	</context-param>
	<web-app>

<!-- more -->

为什么必须进行以上配置？

Web应用服务器tomcat不会为其下不同的web应用使用独立的系统参数；即就是说，应用服务器tomcat上所有的web应用共用一个系统参数对象（webAppRootKey,默认值为"webapp.root"）。运行多个web应用时，你就必须通过 webAppRootKey 上下文参数的不同为不同的web应用指定不同的属性名，如此，才不会造成多个web应用指向同一个webAppRootKey。

如我本地测试，Tomcat同时运行student、teacher两个web项目，我的配置：

	<!-- 项目student的web.xml配置 -->
	<context-param>
		<param-name>webAppRootKey</param-name>
		<param-value>webapp.student</param-value>
	</context-param>

	------------------- 华丽的分割线 -------------------

	<!-- 项目teacher的web.xml配置 -->
	<context-param>
		<param-name>webAppRootKey</param-name>
		<param-value>webapp.teacher</param-value> 
	</context-param>

你可以通过 System.getProperty("webapp.root") 动态获取项目运行路径：

	System.getProperty("webapp.student");	//student project	
	运行结果：D:\workspace\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps\student\

	System.getProperty("webapp.student");	//teacher project
	运行结果：D:\workspace\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps\teacher\
	
	--------------------------------------------------
	 友情提示： " D:\workspace " 为我eclipse的工作空间
	--------------------------------------------------

如果，Tomcat 运行多个web项目不进行webAppRootKey配置（或配置相同的webAppRootKey为webapp.root），将发生如下错误：

	Web app root system property already set to different value: 'webapp.root' 
	= [D:\workspace\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps\student\] 
	instead of [D:\workspace\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps\teacher\] 
	- Choose unique values for the 'webAppRootKey' context-param in your web.xml files!  
	--------------------------------------------------
	 友情提示：方便页面展示，以上错误经过合理的换行处理
	--------------------------------------------------

错误显示大概就是说： key 为 `"webapp.root"` 已经指向项目student, 不能再指向项目teacher，需要在你的web.xml文件<context-param>标签内配置唯一的webAppRootKey值; 所以，web应用服务器Tomcat运行多个web应用，必须对webAppRootKey进行相应的配置。
