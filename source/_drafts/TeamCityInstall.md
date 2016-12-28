title: TeamCityInstall
tags:
---
首先去官网(https://www.jetbrains.com/teamcity/)下载对应操作系统版本安装文件: TeamCity-<version>.tag.gz；安装TeamCity前必须按照JDK；

    $ tar -zxvf TeamCity-<version>.tag.gz -C <dist dir>   # 解压安装包
    $ cd <dist dir>/TeamCity/bin        # 进入TeamCity的bin目录
    $ ./runAll.sh (start | stop [force])    # 启动、停止(强制)

若以上步骤无错即可访问TeamCity界面：<host|ip>:8111，TeamCity默认访问端口为8111；首次访问该地址会进入配置TeamCity的数据目录页：
![设置配置数据目录](../imgs/tc1.png)

默认为：/home/<user>/.BuildServer; 我们使用默认进入下一步；设置存储使用的数据库(默认为HSQLDB)，当然你可选择提供的PostgreSQL\MYSQL\Oracle\MS SQL Server
![选择数据库](../imgs/tc2.png)

我们选择默认下一步；此时，它会初始化数据库及服务组件，稍等片刻即可进入选择协议license页面，点击接受Accept继续；将进入创建用户页面：
![创建用户](../imgs/tc3.png)

填写完用户名密码后创建用户，即可进入“My Setting & Tools”配置个人信息等信息；

点击右上角的"Administration"进入选项Projects即可创建Project；

若需查看更多关于TeamCity的配置，查看本站其他文章。

teamcity在docker的运行：
    
    镜像地址：https://hub.docker.com/r/jetbrains/teamcity-server/
    运行命令：
        docker run -it --name teamcity-server-instance  \
            -v <path to data directory>:/data/teamcity_server/datadir \
            -v <path to logs directory>:/opt/teamcity/logs  \
            -p <port on host>:8111 \
            jetbrains/teamcity-server