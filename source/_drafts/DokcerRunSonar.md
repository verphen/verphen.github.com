title: Dokcer运行Sonar
tags:
---


配置docker sonar5.6.3（不能连接数据库）  mysql.server restart
sonar容器启动的时候会重新创建表结构，所以重新创建数据库sonar即可；dockerfile里面的数据库连接需要使用ip，因为本机ip与docker里面的ip不一样

每个版本的sonar使用的表结构可能不一样？验证sonar5.6.3和sonar6.1，部分表结构确实不一样；

sonar在maven中的配置(公司和家里的配置不一样)？ sonar5.6能否编译jdk1.7
    <profile>
     <id>sonar</id>
     <activation>
       <activeByDefault>true</activeByDefault>
     </activation>
     <properties>
       <sonar.jdbc.driver>com.mysql.jdbc.Driver</sonar.jdbc.driver>
       
       <!-- 可能根本不需要配置用户名密码 -->
       <sonar.login>admin</sonar.login>   
       <sonar.password>admin</sonar.password>
       <sonar.host.url>http://127.0.0.1:9000</sonar.host.url>
     </properties>
   </profile>
