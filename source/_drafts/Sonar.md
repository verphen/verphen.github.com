# **Sonar安装使用**

***

#### Meta Data 
* author ***
* createTime 2016/04/06/18:23

## 简介
<pre>Sonar 是一个用于代码质量管理的开放平台。通过插件机制，Sonar 可以集成不同的测试工具，代码分析工具,
以及持续集成工具。
例如,可以根据其分析插件查看代码可以优化的地方......</pre>

## 安装
	数据库以Mysql、Windows64位系统为例
1. 前往【http://www.sonarqube.org/downloads/】下载 Sonar,如：sonarqube-5.4.zip
2. 解压sonarqube-5.4.zip到指定目录,如D盘根目录
3. 配置D:\sonarqube-5.4\conf\sonar.properties文件(根据实际数据库连接填写，只要提前新建一个sonar数据库即可)<pre>rewriteBatchedStatements=true
useConfigs=maxPerformance
sonar.jdbc.username: sonar
sonar.jdbc.password: sonar
sonar.jdbc.url: jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8
sonar.jdbc.driverClassName: com.mysql.jdbc.Driver</pre>
4. 将mysql-connector-java-5.1.27.jar复制到该路径下 D:\sonarqube-5.4\extensions\jdbc-driver\mysql
5. 以管理员身份运行 D:\sonarqube-5.4\bin\windows-x86-64\StartSonar.bat 文件，最终提示“web is up”则启动成功
6. 访问 http://localhost:9000/ 即可(安装成功)

<hr/>

## 使用
###1、分析项目代码
	以maven项目为例
1. 在maven的settings.xml文件中做如下配置：<pre>
&lt;profile>
    &lt;id>sonar&lt;/id>
    &lt;activation>
        <activeByDefault>true</activeByDefault>
    &lt;/activation>
    &lt;properties>
        <sonar.jdbc.url>
          jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8
        </sonar.jdbc.url>
        <sonar.jdbc.driverClassName>com.mysql.jdbc.Driver</sonar.jdbc.driverClassName>
        <sonar.jdbc.username>sonar</sonar.jdbc.username>
        <sonar.jdbc.password>sonar</sonar.jdbc.password>
        <sonar.host.url>
          http://localhost:9000/
        </sonar.host.url>
    &lt;/properties>
&lt;/profile></pre>
其中：sonar.host.url填写实际Sonar所部署的地址。sonar.jdbc.url亦然。
2. 将需要使用Sonar分析的maven项目先执行<pre>clean install</pre>
3. 若需要Sonar进行覆盖率分析还需要将此maven项目执行<pre>org.jacoco:jacoco-maven-plugin:prepare-agent clean install</pre>Sonar会运行maven中的测试，若测试出错是无法进行覆盖率分析的。默认Sonar无覆盖率分析。
4. 接着对maven项目运行<pre>sonar:sonar</pre>就可以把项目代码进行分析。
5. 访问http://localhost:9000/ （Sonar所部署的对应地址）可以查看项目代码分析结果。
###2、分配用户
1. 首先使用默认管理员登陆Sonar<pre>username:admin<br/>password:admin</pre>
2. 从顶部导航进入Administration-Security-Users方可创建用户。
###3、常用部分
####3.1 Issures(问题)
	经过分析代码后，Sonar会将代码存在的问题展现出来并提供修改意见
1. 从顶部导航进入Issures会陈列所有问题列表。
2. Issueres左侧为筛选菜单，勾选过滤条件可在Issures右侧列表查看具体Issure。
3. Issure中，问题严重等级如下：<pre>Blocker>Critical>Major>Minor>Info
</pre>
4. 初始时，Issure状态为Open，点击Open会有下拉菜单，admin(管理员)可以更改此状态，选项如下：<pre>Confirm - 确认此问题真正成为需要解决的问题<br/>Resolve as false positive - 不认为此Issure成为问题<br/>Resolve as won't fix - 此Issure可以接受，不需要进一步处理<br/>Resolve as fixed - 此问题已解决（通常先assighned后再更改此状态。默认下，非admin管理员也可修改）</pre>
5. 各teammate(组员用户)可以根据情况assighned相应的Issure进行处理。
6. teammate(组员用户)可以在My Account下查看自己的任务及其他情况。
7. 处理完毕更改Issure状态为 Resolve as fixed。
####3.2 Dashboards(仪表盘)
1. 进入Dashboards-Home后，右侧可查看所有已分析的Projects。
2. 点击进入其中一个Project可查看该Project的整体情况。
3. 接着在Technical Debt中的Unmanaged Issures中可查看各个teammate(组员用户)的完成情况。
###4、其他部分
	其他常用功能很容易明白，不再累赘。详细可参考 ——  http://docs.sonarqube.org/display/SONAR/Documentation