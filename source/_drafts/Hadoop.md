1.按照jdk
2.下载hadoop,解压并设置环境变量
3.修改Hadoop的配置文件（hadoop/etc/hadoop/*）
    . hadoop-env.sh
        #export JAVA_HOME=${JAVA_HOME}
        export JAVA_HOME=/usr/java/jdk1.7.0_79

    . yarn-env.sh
        #export JAVA_HOME=${JAVA_HOME}
        export JAVA_HOME=/usr/java/jdk1.7.0_79

    . core-site.xml
        <configuration>
            <property>
                <name>hadoop.tmp.dir</name>
                <value>/sources/hadoop/tmp</value>
                <description>namenode上本地的hadoop临时文件夹</description>
            </property>
            <property>
                <name>fs.default.dir</name>
                <value>hdfs://localhost:7002</value>
                 <description>HDFS的URI，文件系统://namenode标识:端口号</description>
            </property>
        </configuration>


    . hdfs-site.xml
       <configuration>
            <property>
                <name>dfs.name.dir</name>
                <value>/sources/hadoop/hdfs/name</value>
                <description>namenode上存储hdfs名字空间元数据 </description> 
            </property>
            <property>
                <name>dfs.data.dir</name>
                <value>/sources/hadoop/hdfs/data</value>
                <description>datanode上数据块的物理存储位置</description>
            </property>
            <property>
                <name>dfs.replication</name>
                <value>1</value>
                <description>副本个数，配置默认是3,应小于datanode机器数量</description>
            </property>
        </configuration>

        . mapred-site.xml (没有则以mapred-site.xml.template新建)
        <configuration>
            <property>
                    <name>mapreduce.framework.name</name>
                    <value>yarn</value>
            </property>
        </configuration>

4. 格式化Hadoop namenode
    $ bin/hadoop namenode -format 
5. 启动NameNode 和 DataNode 守护进程
    $ sbin/start-dfs.sh
6. 启动ResourceManager 和 NodeManager 守护进程
    $ sbin/start-yarn.sh
7. 验证(可以查看启动的相关进程)
    $ jps 


hdfs: 流式数据访问（一次写入多次读，一旦被写入不会被修改，若需要修改需要删除重新写入）；存储大文件； 适合做数据批量读写、吞吐量高；不适合做交互式应用，低延迟很难满足；适合一次写入多次读取，顺序读写，不支持多用户并发写相同文件；

问题汇总：
    
    Q: mac ssh localhost connection refused
    A: 安装对应系统的SSH服务；若已安装，看是否已打开；我本机为mac(默认关闭ssh localhost)，打开命令`sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist`,查看是否打开`sudo launchctl list |grep ssh`


$ hadoop fs -ls <dir>      # 显示目录的文件信息(如系统的ls命令)
$ hadoop fs -mkdir <dir>    # 创建目录
$ hadoop fs -put <file> <target_dir>    # 上传本地文件至hdfs
$ hadoop fs -cat <file>     # 查看文件
$ hadoop fs -get <file> [new_name]  # 下载文件
$ hadoop dfsadmin -report   # 查看hdfs的使用情况等信息(未尝试成功，待重试)



