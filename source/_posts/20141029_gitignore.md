title: gitignore settings
date: 2014-10-30 07:35:22
categories: tools
tags: [tools,git]
---
Git管理项目，将本地更新提交服务器时，需要忽略某些文件及目录，我们可以再项目根目录下创建创建 `.gitignore`文件，配置该文件即可：

-  .gitignore文件的注释： " # " 开头的行都将被忽略
-  忽略文件夹或者目录： 直接将目录和文件夹放在 .gitignore 文件中即可;每个忽略对象放在一行；如忽略根目录的target文件夹( "target/")、忽略
-  忽略文件：
	-  忽略指定后缀名文件： " *.suffix ",如忽略所有class文件(*.class)


待续...