---
title: 初识Maven
date: 2012-11-22 15:40:12
categories: tools
tags: [tools,maven]
---
今天开始学习怎样使用maven，听起来挺神奇的东西，我们来一步一步的加以剖析。Maven的一些具体的论文的东西，网上很多博客介绍，这里我就不逐一介绍，下面我们从安装maven开始讲解：

- Maven的安装

	首先下载Maven<a href="http://maven.apache.org/download.cgi">(下载地址)</a>（电脑上有以前下载好的，版本是apache-maven-3.0.5，现在就将就这个是用吧），解压到你要安装的目录（我解压到E盘的）。设置环境变量，将bin目录加入到环境变量Path中（如 E:\apache-maven-3.0.5\bin）。现在在dos命令下输入：mvn -v （查看版本信息），如果显示：Apache Maven 3.0.5  、 Maven home: E:\apache-maven-3.0.5\bin\..    、 Java home: E:\Install\JDK\jre （安装maven需要java环境，所以需要提前安装JDK）等信息，则说明你的maven安装成功；否则，检查一下你设置的环境变量，看是否有错误。
-  配置maven的 repository 路径；

  	repository 是存放我们需要用到的库文件，默认路径是在`C:\Users\Administrator\.m2`，一般可以修改该路径，在maven的安装目录下conf文件夹中找到settings.xml（我的在E:\apache-maven-3.0.5\conf\settings.xml），打开该文件在标签“settings”的子标签“localRepository”中内容为你需要存放Repository位置（如`D:\.m2\repository`,也可以复制一份settings出来放在任何位置加以修改）。然后，我运行了一下命令：maven help:system，回车，将下载很多的库文件在r刚刚设置的epository目录下（目前还不清楚这条命令的具体功能，只当做尝试一下)
-  构建一个Eclipse创建的web项目；

	新建一个文件夹（如test），dos进入这个文件夹，输入命令： mvn archetype:create -DgroupId=com.verphen.mavenDemo -DartifactId=chuan -DarchetypeArtifactId=maven-archetype-webapp  创建一个chuan的web项目；这里解释一下上面的这条命令的参数：DartifactId 项目名称（chuan），DgroupId java包名（com.verphen.mavenDemo），如果你没有创建的相关库，输入这条命令将下载相关的库repository ，存放在前面设置repository的位置（我的是E:\apache-maven-3.0.5\repository）。
-  安装将刚刚创建的工程构建成Eclipse创建的工程模样的命令（暂且这么说，初学不知道怎么称呼该命令），安装命令：mvn install eclipse:eclipse ，待相关库及组件下载完成将出现：[INFO]  BUILD SUCCESSFULL ，说明你安装成功。

-  构建Eclipse项目；进入前面创建的文件夹test，执行命令：mvn eclipse:eclipse，即可将创建的项目构建成Eclipse创建的项目，现在你可以将此项目Imporrt Eclipse使用

以上是我初学的简单总结，接下来还会努力去深入学习，欢迎指正！