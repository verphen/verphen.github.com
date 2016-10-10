
ln -s ./pcre_chartables.c.dist pcre_chartables.c


Skipping pcregrep UTF-8 tests: no UTF-8 support in PCRE library  
 这是因为在前面步骤中执行./configuration配置时没有加上对utf-8的支持
$ ./configure --enable-utf8


mvn install -Dgpg.skip
export LC_ALL=en_US.UTF-8

使用flyway-maven-plugin，执行数据库初始化sql文件，和sql数据库升级
[摘要：https://github.com/Dreampie/flyway-maven-plugin 的flyway-maven-plugin插件： 现在方才宣布第一个版本1.0: flyway-maven-plugin.version1.0/flyway-maven-plugin.version 应用体式格局： maven设置装备摆设文件pom.xml里设置装备摆设 plugin groupI] 

https://github.com/Dreampie/flyway-maven-plugin  的flyway-maven-plugin插件：

目前刚刚发布第一个版本1.0:

<flyway-maven-plugin.version>1.0</flyway-maven-plugin.version>
使用方式：

maven配置文件pom.xml里配置

<plugin>         <groupId>cn.dreampie</groupId>         <artifactId>flyway-maven-plugin</artifactId>         <version>${flyway-maven-plugin.version}</version>         <configuration>           <config>${basedir}/src/main/resources/application.properties</config><!--数据库配置文件-->           <location>filesystem:${basedir}/src/main/resources/db/migration/</location><!--数据库sql文件目录-->         </configuration>         <dependencies>           <dependency><!--添加相应的数据库driver-->             <groupId>com.h2database</groupId>             <artifactId>h2</artifactId>             <version>${h2.version}</version>           </dependency>         </dependencies>       </plugin>
application.properties配置数据库 相关参数

devMode = true  db.default.driver=com.mysql.jdbc.Driver db.default.url=jdbc:mysql://192.168.1.211/shm_order?useUnicode=true&characterEncoding=UTF-8 db.default.user=dev db.default.password=dev1010  #db.default.driver=org.h2.Driver #db.default.url=jdbc:h2:file:./db/icedog #db.default.user=sa #db.default.password=file password icedog # Connection Pool settings db.default.poolInitialSize=10 db.default.poolMaxSize=20 db.default.connectionTimeoutMillis=1000 #In production mode, migration is done automatically if db.${dbName}.migration.auto #is set to be true in application.conf. Otherwise it failed to start when migration is needed. db.default.valid.clean=true db.default.migration.auto=true db.default.migration.initOnMigrate=true


该版本支持jdk1.5+，如果不启动项目运行插件，执行命令 cn.dreampie:flyway:1.0:migrate  或者使用ide相应的快捷键,同样可以执行sql





https://github.com/Dreampie?tab=repositories 目录下有多款插件：

cn.dreampie.flyway-maven-plugin     https://github.com/Dreampie/flyway-maven-plugin    flyway-maven数据库升级插件

cn.dreampie.coffeescript-maven-plugin     https://github.com/Dreampie/coffeescript-maven-plugin    coffeescript-maven插件

cn.dreampie.lesscss-maven-plugin     https://github.com/Dreampie/lesscss-maven-plugin    lesscss-maven插件

cn.dreampie.jfinal-shiro     https://github.com/Dreampie/jfinal-shiro    shiro插件

cn.dreampie.jfinal-shiro-freemarker   https://github.com/Dreampie/jfinal-shiro-freemarker    shiro插件实现的freemarker标签库

cn.dreampie.jfinal-web     https://github.com/Dreampie/jfinal-web   相关web插件，简洁model实现

cn.dreampie.jfinal-utils        https://github.com/Dreampie/jfinal-utils   部分jfinal工具

cn.dreampie.jfinal-tablebind        https://github.com/Dreampie/jfinal-tablebind   jfinal的table自动绑定插件，支持多数据源

cn.dreampie.jfinal-flyway      https://github.com/Dreampie/jfinal-flyway   数据库脚本升级插件，开发中升级应用时，使用脚本同步升级数据库或者回滚

cn.dreampie.jfinal-captcha      https://github.com/Dreampie/jfinal-captcha   基于jfinal render的超简单验证吗插件

cn.dreampie.jfinal-quartz       https://github.com/Dreampie/jfinal-quartz   基于jfinal 的quartz管理器

cn.dreampie.jfinal-sqlinxml      https://github.com/Dreampie/jfinal-sqlinxml   基于jfinal 的类似ibatis的sql语句管理方案

cn.dreampie.jfinal-lesscss       https://github.com/Dreampie/jfinal-lesscss   java实现的lesscsss实时编译插件，可以由于jfinal

cn.dreampie.jfinal-coffeescript     https://github.com/Dreampie/jfinal-coffeescript   java实现的coffeescript实时编译插件，可以由于jfinal 

cn.dreampie.jfinal-akka    https://github.com/Dreampie/jfinal-akka   java使用akka执行异步任务

cn.dreampie.jfinal-mailer       https://github.com/Dreampie/jfinal-mailer   使用akka发布邮件的jfinal插件

cn.dreampie.jfinal-slf4j     https://github.com/Dreampie/jfinal-slf4j   让jfinal使用slf4j的日志api




yum groupinstall 命令详解
yum groupinfo []

加密：
https://my.oschina.net/u/724133/blog/299362

yum  -y groupinstall  "Development Tools"


show variables like '%max_connections%';


zabbix安装教程：http://www.360doc.com/content/14/0529/21/8085797_382121204.shtml



GRANT ALL PRIVILEGES ON zabbix.* TO zabbix@localhost IDENTIFIED BY 'zabbix' WITH GRANT OPTION;



待完成：

	同步zabbix的服务器时间（Server  agent）






 http://blog.chinaunix.net/uid-10299986-id-2964493.html

yum -y install 包名（支持*） ：自动选择y，全自动
yum install 包名（支持*） ：手动选择y or n
yum remove 包名（不支持*）
rpm -ivh 包名（支持*）：安装rpm包
rpm -e 包名（不支持*）：卸载rpm包



docker 网络管理：
	docker network create --subnet=172.18.0.0/16 shadownet
	docker network create --subnet=10.0.110.0/24 oraclenet

	docker run --net shadownet --ip 172.18.0.22 --net oraclenet --ip 10.0.110.22 -it testimage /bin/bash
	运行后的容 器只加入到oraclenet里了。	 


mysql中engine=innodb和engine=myisam的区别
