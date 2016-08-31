title: MavenConfigProfile
tags:
---

Maven项目的配置主要集中在pom.xml中，下面我们主要介绍pom文件中配置profile标签:

profile标记是放在profiles标签内，它主要是方便我们在不同的环境下使用多套配置而准备的，如我们测试与生产环境，或者不同团队的环境等等；下面我们看看具体代码

<profiles>
    <profile>
        <!-- 该标签为区别于多个配置 -->
        <id>dev<id>

        # 配置1： JDK环境为1.6时，自动激活构建modules下的子模块； 其他版本JDK则不构建    
        <activation>  
          <jdk>1.6</jdk>  
        </activation>  
        <modules>  
          <module>simple-script</module>  
        </modules>  

        # 配置2： 根据操作系统来自动激活profile
        <activation>  
            # 设置该配置是否为默认配置
            <activeByDefault>false</activeByDefault>  
            <jdk>1.5</jdk>  
            <os>  
              <name>Windows XP</name>  
              <family>Windows</family>  
              <arch>x86</arch>  
              <version>5.1.2600</version>  
            </os>  
            <property>  
              <name>mavenVersion</name>  
              <value>2.0.5</value>  
            </property>  
            <file>  
              <exists>file2.properties</exists>  
              <missing>file1.properties</missing>  
            </file>  
          </activation> 

          # 配置3： 指定外部配置文件(~/.m2/setting.xml或者M2_HOME/conf/setting.xml)
           <activeProfiles>  
            <activeProfile>local_setting.xml</activeProfile>  
          </activeProfiles> 

          # 该标签主要配置项目需要使用的一些常量（如数据库配置、日志路径等等),标签名自定义即可
          <properties>
                <log.path>/home/...</log.path>
          </properties>

    </profile>
</profiles>

若使用maven编译时，手动指定编译的环境配置，可通过-Pxxx(大写P)来指定环境(xxx为profile中的id标签)
    $ mvn clean install -Pdev  # dev为pom.xml中配置的profile内的id标签


