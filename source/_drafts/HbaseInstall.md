title: HbaseInstall
tags:
---

> 安装hbase

  下载hbase安装包(hbase-1.0.3-bin.tar.gz), 解压并配置JAVA环境变量
  $ vi conf/hbase-env.sh

  		export JAVA_HOME=/home/comall/software/jdk1.8.0_73

> 启动hbase shell
  $ cd bin/
  $ ./hbase.sh shell 	# 进入hbase shell，查询hbase shell使用命令(staus、list、status 'detailed'等)
  	$hbase(main):001:0>  


> 配置hbase

	配置文件hbase-site.xml

	<configuration>
		<!-- 配置数据根目录 -->
	   <property>
	        <name>hbase.rootdir</name>
	        <value>file:///home/comall/software/data/hbase</value>
	    </property>

		<!-- web访问端口，默认为16010 -->
	   <property>
	        <name>hbase.master.info.port</name>
	        <value>15000</value>
	    </property>
	</configuration>



>> 给web搭建mysql数据库，然后修改配置在尝试

查看记录	get '表名称', '行名称'
查看表中的记录总数	count  '表名称'
删除记录	delete  '表名' ,'行名称' , '列名称'

- javaagent:../lib/pinpoint-bootstrap-1.5.2.jar -Dpinpoint.agentId=1111 -Dpinpoint.applicationName=firstTest
agent采样开关、频率在$AGENT_PATH下的pinpoint.config中配置


