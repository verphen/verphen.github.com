title: Tomcat 角色
tags:
  - tomcat
  - role
categories: web
date: 2015-07-06 16:04:40
---
tomcat角色使用场景：jenkins的配置、访问tomcat默认的manager\host-manager项目

如你需要访问manager或host-manager项目; 通过地址 ` http://localhost:8080/[manager|host-manager]` 访问，但是需要用户名密码验证：

<img src="/imgs/tomcat/verification.png" alt="Tomcat verification"/>

提示你输入用户名密码进行登录，tomcat默认没有配置用户名密码以及用户角色;具体配置文件: conf/tomcat-user-xml; 只需在该文件的 `<tomcat-users>` 标签内进行如下用户及角色配置即可访问.

<!-- more -->

    <role rolename="manager-gui"/>
    <role rolename="manager-script"/>
    <role rolename="manager-jmx"/>
    <role rolename="manager-status"/>

tomcat的在线documents: http://tomcat.apache.org/tomcat-8.0-doc/manager-howto.html , 查看"Configuring Manager Application Access"栏，官方给出角色的描述：

	manager-gui - allows access to the HTML GUI and the status pages
	manager-script - allows access to the text interface and the status pages
	manager-jmx - allows access to the JMX proxy and the status pages
	manager-status - allows access to the status pages only

当然你还必须配置用户

	<user username="admin" password="admin" roles="manager-gui,manager-script,manager-jmx,manager-status"/>

多个角色之间用逗号(",")隔开

访问host-manager项目需配置角色：

	<role rolename="admin-gui"/>
	<role rolename="admin-script"/>

官方描述：

	admin-gui - allows access to the HTML GUI
	admin-script - allows access to the text interface

tips: Tomcat默认项目 manager/host-manager 的作用

-  manager 项目：   对tomcat应用进行管理，包括对应用进行启动、停止和重启，以及发布新应用和删除已发布应用；设置应用的Expire sessions(session到期时间，默认30分钟)

-  host-manager 项目： 对 tomcat 的虚拟主机进行管理