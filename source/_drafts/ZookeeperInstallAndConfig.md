title: ZookeeperInstallAndConfig
categories: tools
tags: [zookeeper]
---
 介绍：http://zookeeper.apache.org/
 为方便书写，以下所有 zookeeper 以 zk 替换；
 安装：

    # 下载对应版本的zookeeper
    $ wget http://mirrors.hust.edu.cn/apache/zookeeper/current/zookeeper-${version}.tar.gz

    $ tar -zxvf zookeeper-${version}.tar.gz     # 解压文件
    $ cd zookeeper-${version}   # 进入zookeeper根目录
    $ mkdir data logs   # 新建目录data(数据目录)、logs(日志目录)
    $ vi conf/zoo.cfg   # 新建并编辑conf/zoo.cfg文件(zookeeper配置文件，默认不存在)

        tickTime=2000
        dataDir=/usr/local/zookeeper-3.4.9/data
        dataLogDir=/usr/local/zookeeper-3.4.9/logs
        clientPort=2181
        initLimit=5
        syncLimit=2

    # zookeeper基本命令
    $ zkServer.sh {start|start-foreground|stop|restart|status|upgrade|print-cmd}

    $ ./zkServer.sh start  # 启动zookeeper
    $ ./zkServer.sh status # 查看zookeeper启动状态(打印信息出现"Mode: standalone"，表示zk为单点)


zookeeper 集群配置(三台服务器)
    
    # 使用的集群服务器
    10.0.0.21 server1
    10.0.0.22 server2
    10.0.0.23 server3

在每台服务器以单点形式安装zk，然后对每一台服务器zk配置文件 zoo.cfg 添加集群配置：
    
    # server.[myid]:[ip]:[port1]:[port2],表述信息参考博文"zoo.cfg配置"
    server.1:10.0.0.21:2888:3888
    server.2:10.0.0.22:2888:3888
    server.3:10.0.0.23:2888:3888

同时在每台服务器zk的配置目录conf下新建文件myid,同时将上一步配置的“myid”写入文件即可； 即 10.0.0.21 配置的myid文件内容为1，后面两台类推；然后分别启动zk即完成集群配置，zk会自动选举leader及follower（目前的配置会是1台为leader、两台为foller，使用 ` zkServer.sh status `查看）   







