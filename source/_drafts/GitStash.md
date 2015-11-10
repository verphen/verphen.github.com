title: Git Stash
date: 2015-11-05 14:42:43
categories: git 
tags:
  - git
  - stash
---
	
	$ git stash --help 		# 查看帮助

    $ git stash 		# 将当前的改变暂时保存起来

    $ git stash list 		# 查看暂存地的所有的暂存列表

    $ git stash apply 		# 恢复暂存之前的改变，不删除暂存
    $ git stash pop 		# 恢复暂存之前的改变，并删除暂存
    $ git stash drop		# 删除暂存

    $ git stash show
    $ git stash branch <branchname>
    $ git stash clear
    $ git stash create
    $ git stash store

     git reset HEAD~1  重置最新的提交
     git revert HEAD  生成新的commit来revert上次操作
     git rebase -i origin/master   对未同步的代码做“变基”XD
     git rebase -i --abort   "变基"失败可以忽略重来

     git ll    