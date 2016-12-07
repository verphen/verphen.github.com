title: PinpointInstall
tags:
---

官方描述：Pinpoint 是用Java编写的APM（Application Performance Management & Monitoring 应用性能管理&监控）工具，用于大规模分布式系统。在 Dapper 之后，Pinpoint 提供了一个解决方案，以帮助分析系统的总体结构以及分布式应用程序的组件之间是如何进行数据互联的。

安装agent是无侵入式的

对性能的影响最小（只增加约3％资源利用率）

源码地址：https://github.com/naver/pinpoint

参考：https://skyao.gitbooks.io/leaning-pinpoint/content/installation/guide.html

. 安装jdk
	
	必须配置系统变量JAVA_6_HOME、JAVA_7_HOME、JAVA_8_HOME；必须安装jdk8; 若担心系统自带openJDK影响你的安装，可以先卸载` sudo apt-get remove openjdk* `;
	
	#conf java6 envi
	export JAVA_6_HOME=/home/comall/software/jdk1.7.0_79
	export PATH=$JAVA_6_HOME/bin:$PATH
	export CLASSPATH=.:$JAVA_6_HOME/lib/dt.jar:$JAVA_6_HOME/lib/tools.jar

	# conf java7 envi
	export JAVA_7_HOME=/home/comall/software/jdk1.7.0_79
	export PATH=$JAVA_7_HOME/bin:$PATH
	export CLASSPATH=.:$JAVA_7_HOME/lib/dt.jar:$JAVA_7_HOME/lib/tools.jar

	#conf java8 envi
	export JAVA_8_HOME=/home/comall/software/jdk1.8.0_73
	export PATH=$JAVA_8_HOME/bin:$PATH
	export CLASSPATH=.:$JAVA_8_HOME/lib/dt.jar:$JAVA_8_HOME/lib/tools.jar

. 安装maven


. 下载pinpoint源码
	
	git clone https://github.com/naver/pinpoint.git

	进入pinpoint源码目录,编译“mvn install -Dmaven.test.skip=true ”


。 解压hbase-1.0.3到目录/home/comall/software/pinpoint-1.5.2/quickstart/hbase

。快速开始：启动pinpoint自带demo

		。 给hbase添加java环境变量
			$ vi /home/comall/software/pinpoint-1.5.2/quickstart/hbase/hbase/conf/hbase-env.sh
			
				export JAVA_HOME=/home/comall/software/jdk1.8.0_73


		。启动hbase

			$ cd /home/comall/software/pinpoint-1.5.2/quickstart/bin
			$ ./start-hbase.sh 			# 启动hbase； jps可以看到HMaster进程
			$ ./init-hbase.sh 			# 初始化hbase表
			$ ./stop-hbase.sh 			# 停止hbase

		。启动pinpoint的collector
			$ cd /home/comall/software/pinpoint-1.5.2/quickstart/bin
			$ ./start-collector.sh 			#  启动collector; 这个步骤会比较慢，会下载maven的依赖文件，可以tail监控日志文件(tail -f ../logs/quickstart.collector.log)；启动过程中可能会报错，由于无法下载对应的maven的依赖文件，启动成功通过jps命令可以查看到对应的Launcher。
			$ ./stop-collector.sh 			# 停止collector

		。启动web ui
			$ cd /home/comall/software/pinpoint-1.5.2/quickstart/bin
			$ ./start-web.sh 			#  启动web; 这个步骤同样会下载maven依赖文件，查看日志(tail -f ../los/quickstart.web.log)；同样该步骤也可能会报错，由于无法下载对应的maven的依赖文件，启动成功通过jps命令可以查看到对应的Launcher。
			$ ./stop-web.sh 			# 停止web ui

		. 启动测试APP
			$ cd /home/comall/software/pinpoint-1.5.2/quickstart/bin
			$ ./start-testapp.sh 		# 启动一个测试应用，启动过程可以查看日志quickstart.testapp.log监控
			$ ./stop-testapp.sh 		# 停止测试应用testapp

		。访问地址
			Web UI - http://localhost:28080
			TestApp - http://localhost:28081


。结合自身需求定制

	> 安装hbase

	  下载hbase安装包(hbase-1.0.3-bin.tar.gz), 解压并配置JAVA环境变量
	  $ vi conf/hbase-env.sh

	  		export JAVA_HOME=/home/comall/software/jdk1.8.0_73

	> 服务端
	> 将编译pinpoint之后，复制collector.war及web.war放在容器中运行起来(若分开部署可能会出现10080端口冲突)

	


	> 配置agent

		. 上传agent到需要监听的服务器，配置agent/pinpoint.config，修改profiler.collector.ip为你启动collector服务的IP
		. 使用pinpoint-agent/script/networktest.sh脚本来测试网络是否正常

		. 配置tomcat/bin/catalina.sh, 最开始的地方加入下面内容
			AGENT_VERSION="1.5.2"
			AGENT_ID="comall20161111"
			APPLICATION_NAME="firt_pinpoint"
			AGENT_PATH="/home/comall/software/pinpoint-agent-1.5.2"
			CATALINA_OPTS="$CATALINA_OPTS -javaagent:$AGENT_PATH/pinpoint-bootstrap-${AGENT_VERSION}.jar"
			CATALINA_OPTS="$CATALINA_OPTS -Dpinpoint.agentId=$AGENT_ID"
			CATALINA_OPTS="$CATALINA_OPTS -Dpinpoint.applicationName=$APPLICATION_NAME"
	
	注意：agent_id和agent_name不能为中文、中划线



解读：

	Call Tree:
		Gap(ms) : time elapsed between the start of the previous method and entry of this method
				  从上一个方法的开始和该方法的输入之间经过的时间
				  
		Self(ms): the time that was used for execution od this method only, excluding time consumed in nested methods call()
				  仅用于执行此方法的时间，不包括嵌套方法调用中消耗的时间












