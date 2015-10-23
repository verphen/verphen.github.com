title: Git分支
tags:
  - git
  - branch
date: 2015-10-23 22:35:35
categories: git
---

$ git branch --help		# 查看关于git branch帮助
$ git branch name	# 创建name分支

$ git branch --merged 	# 查看已合并的分支列表
$ git branch --no-merged	# 查看未合并的分支列表



- git branch [- a|r...]: 查看本地分支(不带任何参数)，分支名前带星号" * "的是当前分支
	- -a: 查看所有(all)分支（本地及远程分支）
	- -r: 查看远程（remote）分支
	- -d branch-name: 删除(delete)本地分支(分支名：branch-name),该分支必须全部合并到不相关分支,没有未完成的操作
	- -D branch-name: 删除本地分支(分支名：branch-name),无论该分支是否合并到其他不相关分支
	- -r -d origin/remoe-branch-name: 删除远程分支(分支名：remote-branch-name)
	- git push origin :remote-branch-name: 删除远程分支(分支名：remote-branch-name),冒号前面的空格不能少;原理：把空分支push到远程server上,达到删除的结果
	- -m oldName  newName: 重命名(rename)move分支(待命名分支名：oldName;命名成分支：newName) 
- git branch branch-name: 创建分支（分支名:branch-name）