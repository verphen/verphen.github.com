title: Git reset
date: 2015-11-17 14:31:16
categories: git
tags:
  - git
  - reset
---

git reset --hard <commit_id_5>

git reset --hard HEAD^ : 回退到上一版本

          如果回退错误，也可以回退到指定版本  git reset --hard commitId (记住上一版本commitId即可)     


git reset <file> # 从暂存区恢复到工作文件 
git reset -- . # 从暂存区恢复到工作文件 
git reset --hard HEAD^ # 恢复最近一次提交过的状态，即放弃上次提交后的所有本次修改 
git reset --hard <commit id> # 恢复到某一次提交的状态 
git reset HEAD <file> # 抛弃暂存区中文件的修改

git reset HEAD file : 把暂存区的修改撤销掉(unstage), 冲洗放回工作区

放弃工作目录下的所有修改：
$ git reset --hard HEAD

移除缓存区的所有文件（i.e. 撤销上次git add）:
$ git reset HEAD

将HEAD重置到指定的版本，并抛弃该版本之后的所有修改：
$ git reset --hard <commit>

$ git reset - -hard  HARD<~|^><n> 	# 回退n次提交；（n可以用符号~、^的个数表示回退次数）

将HEAD重置到上一次提交的版本，并将之后的修改标记为未添加到缓存区的修改：
$ git reset <commit>

将HEAD重置到上一次提交的版本，并保留未提交的本地修改：
$ git reset --keep <commit>

git reset HEAD <file>       # 取消已暂存文件的修改

git reset --hard SHA
–hard 回退版本，代码也回退，忽略所有修改
–soft 回退版本，代码不变，回退所有的 add 操作
–mixed 回退版本，代码不变，保留 add 操作


git reset 回溯


git reflog 查看操作历史

