title: git 克隆
tags:
  - git
  - command
date: 2015-09-16 22:35:35
categories: git
---

	$ git help 		# Git帮助(常用的Git命令及描述)

	$ git help <command>    # 显示command命令的帮助

	$ git <command>  --help   # 以HTML显示command命令详细帮助(Launching default browser to display HTML ...)

    $ git show [commitID]   # 显示上一次提交详细差异信息[指定版本的差异信息]

    $ gitk  #  可视化界面查看提交记录等

克隆本地仓库： git clong /path/repository
克隆远程仓库： git clone username@hostname:/path/repository

https://github.com/xirong/my-git/blob/master/how-to-use-github.md

git clone <url> [project_name]      # 从现有仓库中克隆