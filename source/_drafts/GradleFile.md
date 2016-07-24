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