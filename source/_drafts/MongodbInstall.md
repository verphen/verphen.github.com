title: MongodbInstall
tags:
---
首先去[MongoDB官网](https://www.mongodb.com/download-center#community)下载安装包

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


