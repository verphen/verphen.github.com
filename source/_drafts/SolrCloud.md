title: SolrCloud
tags:
---


zookeeper搭建： http://blog.csdn.net/shirdrn/article/details/7183503




solr搭建集群：http://blog.csdn.net/xyls12345/article/details/27504965

solr集群搭建之前必须先搭建zookeeper集群；

1. 修改tomcat的启动文件catalina.sh （添加java启动参数的地方）
	
    (主) JAVA_OPTS="$JAVA_OPTS -Dbootstrap_confdir=/home/comall/software/solrhome/songshu-dev/conf -Dcollection.configName=myconf -DzkHost=10.0.0.19:2181,10.0.0.22:2181,10.0.0.23:2181"


	（从） JAVA_OPTS="-DzkHost=10.0.0.19:2181,10.0.0.22:2181,10.0.0.23:2181"


2. 打开tomcat/webapp/solr/WEB-INF/web.xml, 取消标签<env-entry>的注释，修改env-entry-value为solrhome目录（如/home/comall/software/solrhome）

3. 修改solrhome/solr.xml为如下

		 <solrcloud>
		    <str name="host">${host:10.0.0.16}</str>   	<!-- 本机IP -->
		    <int name="hostPort">${jetty.port:8080}</int> 	<!-- tomcat的访问端口 -->
		    <str name="hostContext">${hostContext:solr}</str>
		    <int name="zkClientTimeout">${zkClientTimeout:30000}</int>
		    <bool name="genericCoreNodeNames">${genericCoreNodeNames:true}</bool>
		  </solrcloud>

		  <shardHandlerFactory name="shardHandlerFactory"
		    class="HttpShardHandlerFactory">
		    <int name="socketTimeout">${socketTimeout:0}</int>
		    <int name="connTimeout">${connTimeout:0}</int>
		  </shardHandlerFactory>

4. 向solr的collection


issuse: 
	在collecgion/core.properties的配置参数含义：

		#Written by CorePropertiesLocator
		#Tue Mar 03 19:10:26 CST 2015
		name=songshu-dev
		config=solrconfig.xml
		schema=schema.xml
		dataDir=/home/comall/software/solrhome/songshu-dev/data
