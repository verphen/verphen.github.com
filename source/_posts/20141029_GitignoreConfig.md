title: gitignore config
date: 2014-10-30 07:35:22
categories: tools
tags: [tools,git]
---
Git管理项目，将本地更新提交服务器时，需要忽略某些文件及目录，我们可以在项目根目录下创建创建 `.gitignore`文件(创建命令 touch .gitignore)，配置该文件即可：

<h4>Be carefull: </h4>

-  .gitignore文件中忽略规则必须顶格写，否则不生效；规则行尾不能再添加注释

-  忽略规则只对未加入git管理的文件生效;若需要忽略文件已经加入git管理，使用 ` git rm -r -n --cached name` 将name(文件或目录)移除git管理(将其从git暂存区域移除)，具体命令详情参考《 Git Commands 》博文 

<h4>具体忽略规则：</h4>

-  .gitignore文件的注释： " # " 开头的行都将被忽略

-  忽略文件夹或者目录： 直接将目录和文件夹放在 .gitignore 文件中即可;每个忽略对象放在一行；如忽略根目录的target文件夹( "target/")、忽略

-  忽略文件：
	-  忽略指定后缀名文件： " *.suffix ",如忽略所有class文件(*.class)