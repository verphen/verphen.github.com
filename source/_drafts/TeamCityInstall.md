title: TeamCity安装
tags:
---
TeamCity安装很简单，安装之前必须先安装JDK；首先去官网(https://www.jetbrains.com/teamcity/)下载对应系统版本文件: `TeamCity-<version>.tag.gz`，我下载的版本为10.0.4；然后按如下步骤进行：

    $ tar -zxvf TeamCity-<version>.tag.gz -C <dist dir>   # 解压安装包
    $ cd <dist dir>/TeamCity/bin        # 进入TeamCity的bin目录
    $ ./runAll.sh (start | stop [force])    # 启动、停止(强制)

若以上步骤无错即可访问TeamCity界面：` <Host|IP>:8111 `，其默认访问端口为8111；若需修改参考(修改配置文件前需停止TeamCity，修改完成再重新启动)：

	$ vi TeamCity/conf/server.xml 		# 编辑server.xml配置文件

![配置访问端口](../imgs/tcc1.png)

首次访问该地址会进入配置TeamCity的数据目录页：
![设置配置数据目录](../imgs/tc1.png)

数据目录默认为`/home/<user>/.BuildServer`，若需修改参考：

	# 修改配置文件属性teamcity.data.path即可
	$ vi TeamCity/conf/teamcity-startup.properties
	
我们使用默认目录进入下一步；设置存储使用的数据库(默认为HSQLDB)，当然你可选择其提供的PostgreSQL\MYSQL\Oracle\MS SQL Server
![选择数据库](../imgs/tc2.png)

我们选择默认数据库进入下一步；此时，它会初始化数据库及服务组件，稍等片刻即可进入选择协议license页面，点击接受Accept继续；将进入创建用户页面：
![创建用户](../imgs/tc3.png)

填写完用户名密码后创建用户，即可进入“My Setting & Tools”配置个人信息等信息，点击右上角的"Administration"进入选项Projects即可创建Project；至此，TeamCity的安装说明已介绍完成。