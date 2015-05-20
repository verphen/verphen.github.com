title: Tomcat Configure
date: 2015-03-05 22:41:00
categories: web
tags: [tomcat]
---
项目开发都在使用tomcat作用web容器，本文简单介绍tomcat的配置，当做总结

- 配置 /conf/server.xml 文件
	
	- 地址栏省略项目名访问web项目（即：地址栏只输入域名或 `localhost:8080` 即可访问web项目）
		
		在 ` <Host> </Host>` 标签中添加如下内容，

			<Context docBase="student" path="" reloadable="true" source="org.eclipse.jst.jee.server:student"/>
	- ds
	
- 配置 context.xml