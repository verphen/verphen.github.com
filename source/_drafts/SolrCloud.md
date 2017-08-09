title: SolrCloud
tags:
---



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


issues: 
	在collecgion/core.properties的配置参数含义：

		#Written by CorePropertiesLocator
		#Tue Mar 03 19:10:26 CST 2015
		name=songshu-dev
		config=solrconfig.xml
		schema=schema.xml
		dataDir=/home/comall/software/solrhome/songshu-dev/data



公司搭建solrcloud记录：


 
solrcloud

	solr

		solr-tomcat8-1 	8010 、8015、8019
		solr-tomcat8-2 	8020 、8025、8029
		solr-tomcat8-3 	8030 、8035、8039

	zk

		server.1=10.0.0.6:2888:3888
		server.2=10.0.0.6:2889:3889
		server.3=10.0.0.6:2890:2890





>  配置zk集群

> 上传solr配置文件至zk
	。设置 org.apache.solr.cloud.ZkCLI 到环境变量 （D:\solr621\apache-tomcat-8.0.39\webapps\solr\WEB-INF\lib\*）
	。执行java方法并上传solr配置文件(conf目录包含 solrconfig.xml 及 schema.xml文件)；(参数-classpath已经设置环境变量)

		java -classpath .:/usr/local/solrcloud-4.7.2/solr-tomcat8-server2/webapps/solr/WEB-INF/lib/*  org.apache.solr.cloud.ZkCLI -cmd upconfig -zkhost 127.0.0.1:2181,127.0.0.1:2182,127.0.0.1:2183/shopping -confdir /local/solrcloud-4.7.2/packages/conf  -confname product

		(java -classpath 等同于 java -cp)

> 安装solr
	。上传solr.war到webapps
	。修改web.xml的solrhome；复制
	。添加log4j.propertis,并修改日志路径（ 参考 ${CATALINA_HOME} 即就是tomcat根目录 ）
	。添加solr.xml到solrhome的根目录

> 创建集合
	
	。删除solr集群所有节点solrhome下的集群数据(collection_shard_replica)

	。solr集群的任一节点执行就可以
	http://localhost:8010/solr/admin/collections?action=CREATE&name=product&numShards=3&replicationFactor=2&collection.configName=product&maxShardsPerNode=3


注意：

	。 配置schema.xml时，field标签配置属性的type必须为标签fieldType配置的name值，区分大小写
	。 schema.xml必须配置field为“_version_”的内容，如

			<field name="_version_" type="long" indexed="true"  stored="true" multiValued="false" />


熟悉solrj 、 solrconfig.xml 、 schema.xml



解析：http://192.168.0.61:8080/solr/article_shard2_replica2/addDic=可卖
	 上面的URL的执行，只对article集合的shard2_replica2对应的机器生效，如果shard2_replica2不在本机（192.168.0.61），则本机的JVM不存在URL执行后添加的词条

	 

