title: MongodbInstall
tags:
---
首先去[MongoDB官网](https://www.mongodb.com/download-center#community)下载安装包; 参考(http://jingyan.baidu.com/article/0a52e3f4217e65bf62ed729a.html)

    # 安装目录：/usr/local
    cd /usr/local

    # 解压安装文件
    $ tar -zxvf mongodb-xxx.tgz

    # 重命名解压文件夹
    $ mv mongodb-xxx    mongodb

    # 创建mongodb存放数据的文件夹db和日志文件夹logs
    $ mkdir  db  logs

    # 创建mongodb的配置文件,并添加内容
    $ vi mongodb.conf

        # 数据文件目录
        dbpath=/usr/local/mongodb/db
        # 日志目录
        logpath=/usr/local/mongodb/logs/mongodb.log
        # 端口
        port=27017
        fork=true
        nohttpinterface=true




微软云mongodb1的启动配置mongodb.conf ：

        dbpath=/home/comall/mongodb/data   #数据存放目录  
        logpath=/home/comall/mongodb/logs/mongod.log  #日志文件目录  
        pidfilepath=/home/comall/mongodb/mongod.pid  #pid端口文件  
          
        port=27017   #mongodb端口  
          
        logappend=true   #追加方式写日志文件  
        fork=true        #后台运行  
        journal=true     #启用日志选项，MongoDB的数据操作将会写入到journal文件夹的文件里  
        oplogSize=2048   #同步操作记录文件大小(MB)  
        smallfiles=true  #使用较小的默认文件  
          
        replSet=test    #副本集名称，同一个副本集，名称必须一致  






# 启动
$ ./mongod < - -config | -f > mongodb.conf

        
        
2. 启动mongodb出现的错误解决方案

    。 ./mongod: error while loading shared libraries: libssl.so.6: cannot open shared object file: No such file or directory
    
    解决方案：
    
        # 创建软链接（参考 http://www.jiaozn.com/reed/19.html）
        $ ln -sf /usr/lib64/libssl.so.10 /usr/lib64/libssl.so.6
        $ ln -sf /usr/lib64/libcrypto.so.10 /usr/lib64/libcrypto.so.6
      
    。2016-06-08T08:56:11.619+0000 F CONTROL  [main] Failed global initialization: BadValue: Invalid or no user locale set. Please ensure LANG and/or LC_* environment variables are set correctly.
    
    解决方案：
    
        # 清除当前shell所有本地化的设置，让命令能正确执行
        $ export LC_ALL=C   
