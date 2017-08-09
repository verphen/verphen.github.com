title: zoo.cfg 配置
categories: tools
tags: [zookeeper,config]
---
对zookeeper的配置文件zoo.cfg的配置属性描述：

-  tickTime=2000
	# 基本事件单元，以毫秒为单位; 作为 Zookeeper 服务器之间或客户端与服务器之间维持心跳的时间间隔，也就是每个 tickTime 时间就会发送一个心跳


# Zookeeper接受客户端（这里所说的客户端不是用户连接Zookeeper服务器的客户端,而是Zookeeper服务器集群中连接到Leader的Follower务器）初始化连接时最长能忍受多少个心跳时间间隔数，当已经超过 5 个心跳的时间（也就是tickTime）长度后 Zookeeper 服务器还没有收到客户端的返回信息，那么表明这个客户端连接失败; 总的时间长度就是 5\*2000=10 秒。
initLimit=5

# 标识 Leader 与 Follower 之间发送消息，请求和应答时间长度，最长不能超过N个 tickTime 的时间长度，总的时间长度就是 2\*2000=4 秒
syncLimit=2

# 存储内存中数据库快照的位置，顾名思义就是 Zookeeper 保存数据的目录，默认情况下，Zookeeper 将写数据的日志文件也保存在这个目录里。
dataDir

# 日志目录，若不配置默认为dataDir
dataLogDir

# 客户端连接 Zookeeper 服务器的端口，Zookeeper 会监听这个端口，接受客户端的访问请求
clientPort=2181

# 定时清理snapshot和事务日志的功能(即目录dataDir与dataLogDir)
autopurge.purgeInterval # 清理频率，单位是小时，需要填写一个1或更大的整数，默认是0，表示不开启自己清理功能。
autopurge.snapRetainCount   # 该参数和上面的参数（purgeInterval）搭配使用，指定需要保留的文件数目，默认是保留3个

# 表示这个是第几号服务器,B 是这个服务器的 ip 地址；C 表示的是这个服务器与集群中的 Leader 服务器交换信息的端口；D 表示的是万一集群中的 Leader 服务器挂了，需要一个端口来重新进行选举，选出一个新的 Leader
server.A = B:C:D : A 