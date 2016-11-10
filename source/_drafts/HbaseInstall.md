title: HbaseInstall
tags:
---

> 安装hbase

  下载hbase安装包(hbase-1.0.3-bin.tar.gz), 解压并配置JAVA环境变量
  $ vi conf/hbase-env.sh

  		export JAVA_HOME=/home/comall/software/jdk1.8.0_73

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