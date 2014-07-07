title: 2014.7.7_Eclipse生成JavaDoc
date: 2014-07-07 15:30:21
categories: Tools
tags: [java,工具,eclipse]
---
项目开发中有时需要一览整个项目的类、方法的文档说明，此时可以使用JavaDoc来临时补缺没有文档的烦恼；下面介绍在Eclipse中导出JavaDoc的几种方法，其实都是殊途同归(不同的方式打开Javadoc Generation向导页进行配置)：

<!--more-->

### 打开Javadoc Generation向导页
1. Eclipse菜单栏 --> Project --> Generate javadoc出现Javadoc Generation向导页

2. 选择需要生成Javadoc的项目右键Export，选择Java选项的下javadoc即可出现Javadoc Generation向导页 

###配置Javadoc Generation向导页

1. 在Javadoc command选项配置 `jdk\bin\javadoc.exe`；
2. 选择需要导出Javadoc的项目(注意：需要展开项目目录查看是否所有的文件都选中)；
3. 在选项 create javadoc for members with visibility选择默认的 "public"即可；
4. 选择Use standard doclet的Destination选择导出Javadoc的目标地址；
5. 一直点击next到Javadoc Generation的最后一个向导页,在Extra javadoc options选项加入`-encoding utf-8  -charset utf-8` 点击Finish即可。