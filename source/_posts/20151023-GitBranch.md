title: Git 分支
tags:
  - git
  - branch
categories: git
date: 2015-10-23 22:35:35
---
	$ git branch --help     # 查看关于git branch帮助

[查看分支]

	$ git branch    # 查看本地分支（星号*标注为当前分支）
	$ git branch -r     # 查看所有远程[remote]分支
	$ git branch -a     # 查看所有[all]本地及远程分支
	$ git branch -v     # 查看各个分支最后的提交
	$ git branch -vv    # 在[-v]参数结果增添本地分支对应的远程分支

[创建\切换\重命名分支]

	$ git branch <new_branch>       # 创建新分支(继承当前分支最新提交来创建)
	$ git branch <new_branch>  commit_id  # 以指定的提交版本commit_id来创建新分支
	$ git checkout <branch>     # 切换分支
	$ git checkout [commit_id] -b <new_branch>      # 继承当前分支最后一次提交(或指定某次提交)创建并切换到新分支
	$ git checkout <commit_id>      # 切换到某次提交，无分支信息；若再切换回分支则会丢弃切换之前的修改
	$ git checkout -b <new_branch> <master> # 继承master分支创建并切换新分支
	$ git branch -m <branch> <new_branch>       # 重命名分支

[删除分支]

	# 删除本地分支
	$ git branch [-d | -D] <branch>
	    -d      # 删除[delete]本地n支(存在修改或未合并删除失败,多个分支用空格分隔)
	    -D      # 忽略修改强制删除本地分支（多个分支用空格分隔）
	
	# 删除远程分支
	$ git branch -d -r origin/<branch>  # 删除远程分支
	$ git push origin :<branch>     # 冒号前面的空格不能少,即把空分支push到远程达到删除效果[since Git v1.5.0]
	$ git push origin --delete <branch>     # [since Git v1.7.0]

[合并分支]

	$ git branch --merged   # 查看已合并的分支列表
	$ git branch --no-merged    # 查看未合并的分支列表
	$ git merge <branch>    # 合并其他分支到当前分支,发生冲突修复后再次提交

[关联分支]

	# 设置本地分支跟踪远程分支(与远程分支关联)，分支设置跟踪后直接git pull、git push即可直接查找到远程分支进行操作
	$ git branch --set-upstream-to=origin/<branch> <branch>  (推荐)
	$ git branch --set-upstream <branch> <origin/branch>    
 
本地跟踪远程分支，会在当前项目的config文件产生如下配置

	[branch "master"]
	    remote = origin
	    merge = refs/heads/master