title: MongodbCommands
tags:
---

db.help()           获取mongoDB客户端命令列表
db.stats()          获取mongoDB的统计信息

use database_name           创建数据库(存在直接返回)
db.dropDatabase()       删除默认选中的数据库

db.createCollection(name)        创建集合（name为集合名称）
show collections       显示已创建的集合列表

mongod -f <配置文件>        #启动mongodb
mongo  host:port/database      #使用官方提供的客户端mongo连接mongoDB
db.shutdownServer()           #停止mongodb服务

> mongo连接mongoDB
     show dbs          # 查看存在的数据库
     show collections / tables      # 显示表（集合）
     show db.collection_name.getIndexes()      查看索引
     use  <db>           # 切换数据库
     db.dropDatabase()      删除数据库

     db.name.insert({ <json数据> })           name为集合(理解为表)
          $ for(i=3; i<100; i++)db.name.insert({x:i})           循环插入数据
     db.name.find()               查询name集合的所有数据
     db.name.find().count()           查询总记录数
     db.name.find().skip(2).limit(3).sort({x:1})      跳过2条显示3条按字段“x”升序排序[1升序|-1降序]
     db.name.update(<查找条件>, <待更新内容>)     更新
          $ db.name.update({x:1}, {x:999})          更新x=1为x=999（只更新了一条）
     db.name.update(<查找条件>，$set:<更新字段内容>)      部分更新使用$set,字段存在即更新；不存在保持原样
     db.name.update(<查找条件>, <更新内容>， true)          更新不存在数据就创建一条
     db.name.update(<查找条件>, {$set:<更新内容>}, false, true)          更新所有符合的数据

     db.name.remove(<查找条件>)          删除符合条件的所有记录
     db.table_name[collection_name].drop()      删除集合[表]

     。索引
     db.collection_name.ensureIndex(<json数据>)     创建索引
          $ db.collection_name.ensureIndex({x:1})  1表示升序