title: DebugLingLiProgect
date: 2024-04-28 09:50:39
updated: 2024-04-28 09:50:39
categories:
tags:
---

调试灵力项目：

安装项目所需依赖命令：pip install -r requirements.txt


项目requirements.txt相关操作：
	。安装项目依赖：pip install -r requirements.txt
	。生成requirements.txt：
		。安装pipreqs：pip install pipreqs
		。生成requirements.txt文件：pipreqs ./ --encoding=utf8 --force


安装过程问题收集：
。安装pipreqs出现无权限"PermissionError: [Errno 13] Permission denied"
	
	# 执行命令后面添加"--user"即可
	$ pip install pipreqs --user


。安装完成pipreqs，执行该命令显示无此命令
	$ bash: pipreqs: command not found

	# 解决方法：将命令目录加入系统环境变量
	$ pip show pipreqs  # 复制Location地址，替换路径尾部的"site-packages"为"Scripts"


