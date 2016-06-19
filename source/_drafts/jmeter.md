# 启动zookeeper
$ sh zkServer.sh start


# 查看zookeeper状态
$ sh zkServer.sh status


启动mongodb错误
[comall@cm-mongodb1 bin]$ ./mongod --config mongodb.conf
2016-06-17T02:35:29.206+0000 F CONTROL  Failed global initialization: BadValue Invalid or no user locale set. Please ensure LANG and/or LC_* environment variables are set correctly.


jmeter使用上一次response作为下一次入参



-----------

Jmeter做性能测试的时候，需要处理某一方法response数据作为下一个方法的入参，
基于这个需求与不同返回值数据格式我们有三种方式来解决;

tips: 我们使用的工具 [apache-jmeter-3.0](https://jmeter.apache.org/download_jmeter.cgi)

1. 使用正则表达式


	http://www.cnblogs.com/scarlett-hy/articles/4244055.html

2. 使用插件JSON Path Extractor(针对json数据返回值)

    https://github.com/jayway/JsonPath



3. 使用java脚本

 
