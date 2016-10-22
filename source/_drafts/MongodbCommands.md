title: MongodbCommands
tags:
---

db.help()           获取mongoDB客户端命令列表
db.stats()          获取mongoDB的统计信息

use database_name           创建数据库(存在直接返回)
db.dropDatabase()       删除默认选中的数据库

db.createCollection(collection_name)        创建集合
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

     > db.collection_name.insert(document)           name为集合(document为json数据)
          $ for(i=3; i<100; i++)db.name.insert({x:i})           循环插入数据
     > db.collection_name.save(document)；  save和insert方法都是向集合插入文档(document为json数据)

    > db.collection_name.find()    查询集合的所有数据(以非机构化显示，如需要格式化显示使用pretty)

    > db.collection_name.find(document,{key:1,_id:0})   查询条件为document的数据，且结果只显示列key,不显示列_id(该列默认都会显示，需要设置才会不显示)
  
    > limit(number)   限制结果显示个数
    > skip(number)    查询结果跳过第n个记录
    > sort({key:1,key1:-1})   查询结果排序(默认为升序1，-1为降序)
    > 

          $ db.collection_name.find().pretty()    

    > db.collection_name.findOne()  返回第一个document
    > and的实现
      $ db.collection_name.find({key1:value1,key2:value2})    多条件同时满足的查询

    > OR 的实现
      $ db.collection_name.find({
          $or: [{key1:value1},{key2:value2}]
        })
    
     

     db.collection_name.find().count()           查询总记录数
     db.collection_name.find().skip(2).limit(3).sort({x:1})      跳过2条显示3条按字段“x”升序排序[1升序|-1降序]
     db.collection_name.update(<查找条件>, <待更新内容>)     更新
          $ db.name.update({x:1}, {x:999})          更新x=1为x=999（只更新了一条）
     db.collection_name.update(<查找条件>，$set:<更新字段内容>)      部分更新使用$set,字段存在即更新；不存在保持原样
     db.collection_name.update(<查找条件>, <更新内容>， true)          更新不存在数据就创建一条
     db.collection_name.update(<查找条件>, {$set:<更新内容>}, false, true)          更新所有符合的数据

     db.collection_name.remove(<查找条件>)          删除符合条件的所有记录
     
     > db.collection_name.drop()      删除集合  返回值为[true|false]
     


     。索引
     db.collection_name.ensureIndex(<json数据>)     创建索引
          $ db.collection_name.ensureIndex({x:1})  1表示升序, -1表示降序
     $ db.collection_name.dropIndex(<json数据>)     删除索引
     $ db.collection_name.getIndexes(<json数据>)     获取索引
     
     。唯一索引;在缺省情况下创建的索引均不是唯一索引
     $ db.collection_name.ensureIndex({"userid":1},{"unique":true})


     。 使用explain查看查询使用索引之后的细节；explain会返回查询使用的索引情况，耗时和扫描文档数的统计信息。
    
              "cursor":"BasicCursor"表示没有使用索引。
              "nscanned":1 表示查询了多少个文档。
              "n":1 表示返回的文档数量。
              "millis":0 表示整个查询的耗时。


     system.indexes集合中包含了每个索引的详细信息，因此可以通过下面的命令查询已经存在的索引，如：
     > db.system.indexes.find()


