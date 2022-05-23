title: GradleFile
tags:
---


gradew和gradle.bat分别是linux的shell脚本和windows批处理文件，它们的作用是根据gradle-wrapper.properties文件中的distributionUrl下载对应的gradle版本。这样就能够保证在不同的环境下构建时都是使用的统1版本的gradle，即便该环境没有安装gradle也能够，由于gradle wrapper会自动下载对应的gradle版本。gradlew的用法跟gradle1模1样，比如履行构建gradle build命令，你可以用gradlew build。gradlew即gradle wrapper的缩写。

创建一个空目录，依照Maven规范创建项目目录
    
    $ vi build.gradle   # 创建文件并编辑

      `apply plugin: 'java'`

技巧： build.gradle文件的注释和Java注释语法一样;

    // 单行注释

    /*
    * 多行注释
    */

    /**
    * 多行注释
    */




gradle通过pom.xml生成的grade项目文件gradlew及gradle.bat文件的用处
           http://sulong.me/2011/01/26/greate_gradle
           http://sulong.me/2011/08/03/use_cobertura_in_gradle_in_a_better_way

gradle学习：
      http://my.oschina.net/zjzhai/blog/220028
     http://pkaq.github.io/gradledoc/docs/userguide/userguide.html
     http://www.blogjava.net/wldandan/archive/2012/07/05/382246.html
     http://bloodwolf-china.iteye.com/blog/1779681

 gradle2和1的区别
http://blog.csdn.net/column/details/gradle-translation.html?&page=2
http://gradledoc.qiniudn.com/1.12/userguide/userguide.html
http://www.blogjava.net/wldandan/archive/2012/07/05/382246.html

http://pkaq.github.io/2013/12/03/gradleforjenkins/
http://www.cnblogs.com/CloudTeng/p/3417762.html?ADUIN=851474818&ADSESSION=1410338045&ADTAG=CLIENT.QQ.5353_.0&ADPUBNO=26381



