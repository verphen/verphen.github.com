title: Solr for Tomcat 单点安装
tags:
---
环境准备：
1. 安装JDK1.8、tomcat8.5.14
	2. 下载并解压 solr-6.5.1

安装solr到tomcat
1. 复制solr-6.5.1/server/solr-webapp下的webapp到tomcat的webpp目录，并改名为solr（或者为其他，本文修改为ROOT）
2. 修改web.xml文件；在上一步改名的solr文件夹下 solr/WEB-INF/web.xml
	。配置solr的solrhome: 在tomcat根目录新建目录solrhome(你可以创建该目录在任何位置)，复制solr-6.5.1/server/solr目录下所有文件至solrhome目录(否则无法访问)；取消web.xml标签’\<env-entry\>’的注释，并修改标签‘\<env-entry-value\>’的内容为刚创建目录的路径  
	。注释权限管理编辑：数值web.xml的编辑‘\<security-constraint\>’   
3. 在tomcat/webapp/solr/WEB-INF/目录创建classes目录，并复制日志文件solr-6.5.1/server/resources/log4j.properties文件至该目录；并修改该文件内容‘solr.log=${solr.log.dir}’为 ‘solr.log=/tomcat/logs’（修改日志目录到tomcat的日志目录，可配置自定义目录）
4. 复制依赖包：复制solr-6.5.1/server/lib/ext/目录下所有文件至tomcat/webapp/solr/WEB-INF/lib目录，同时将solr-6.5.1/server/lib/目录下metrics开头的文件同样复制到以上tomcat目录（metrics-\*.jar，不复制这几个文件服务访问solr主页）

注意事项：
。访问solr主页（[http://localhost:8080\[/solr]/index.html][1]）必须加上’/index.html’才能正常访问，否则无法访问solr主页


[1]:	http://localhost:8080/index.html#/