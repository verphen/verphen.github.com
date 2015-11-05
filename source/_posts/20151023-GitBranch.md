title: Git 分支
tags:
  - git
  - branch
categories: git
date: 2015-10-23 22:35:35
---
	$ git branch --help		# 查看关于git branch帮助

[查看分支]

	$ git branch 	# 查看本地分支（星号*标注为当前分支）
	$ git branch -r 	# 查看所有远程[remote]分支
	$ git branch -a 	# 查看所有[all]本地及远程分支

[创建\切换\重命名分支]

	$ git branch <dev>		# 创建dev分支(继承当前分支来创建)
	$ git checkout <dev> 	# 切换分支到dev(分支dev需已存在)
	$ git checkout -b <dev>		# 创建分支dev并切换到该分支(前提dev分支不存在)
	$ git checkout -b <dev> <master>	# 创建分支dev并切换到该分支，继承master分支创建而来
	$ git branch -m <dev> <test>		# 重命名dev分支为test

[删除分支]

	# 删除本地分支[dev]
	$ git branch [-d | -D] <dev>
		-d 		# 删除[delete]本地dev分支(存在修改或未合并删除失败,多个分支用空格分隔)
		-D 		# 忽略修改强制删除本地dev分支（多个分支用空格分隔）

	# 删除远程分支[dev]
	$ git branch -d -r <origin/dev> 	# 删除远程分支dev
	$ git push origin :<dev> 	# 冒号前面的空格不能少,即把空分支push到远程达到删除效果[since Git v1.5.0]
	$ git push origin --delete <dev> 	# [since Git v1.7.0]

[合并分支]

	$ git branch --merged 	# 查看已合并的分支列表
	$ git branch --no-merged	# 查看未合并的分支列表
	$ git merge <dev> 	# 合并dev分支到当前分支,发生冲突修复后再次提交

[关联分支]

	$ git branch --set-upstream <dev> <origin/dev>	# 设置本地分支dev与远程分支origin/dev关联1