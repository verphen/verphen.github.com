title: "GitMerge"
date: 2015-11-17 15:04:22
categories: git
tags:
  - git
  - merge
---

git merge <branch> # 将branch分支合并到当前分支 
git merge origin/master --no-ff # 不要Fast-Foward合并，这样可以生成merge提交 
git merge --no-commit <branch> # 合并但不提交 
git merge --squash <branch> # 把一条分支上的内容合并到另一个分支上的一个提交

git merge --no-ff -m "merge info" dev: 不使用Fast forward模式合并分支（Git就会在merge时生成一个新的commit）

 将远程服务器代码取回本地： 
                  git merge [local branch1]     （合并远程更新到本地分支）
                  git merge --no-ff branch     

merge分支用 --no-ff

使用配置好的merge tool 解决冲突：
$ git mergetool
在编辑器中手动解决冲突后，标记文件为已解决冲突

git mergetool                   # GUI方式处理合并冲突

Merge feature branch时请不要使用fast forward



     git reset HEAD~1  重置最新的提交
     git revert HEAD  生成新的commit来revert上次操作
     git rebase -i origin/master   对未同步的代码做“变基”XD
     git rebase -i --abort   "变基"失败可以忽略重来

     git ll    