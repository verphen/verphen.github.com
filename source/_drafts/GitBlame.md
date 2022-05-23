---
title: Git Blame
date: 2015-11-26 11:42:14
categories: web 
tags: [nodejs,windows,ubuntu]
---


	$ git blame <file> 		# 显示文件每行最后提交信息


	




git gc --auto   git垃圾回收

git reset    - - hard HEAD^ (HEAD^^ 同 HEAD~2)
git reflog  

git reflog --回退版本之后反悔了，返回之前的操作

fsck(file system check) :  git fsck --lost-found  检查丢失的提交     
git show [commit_hash]  显示某次提交的改动

git 衍合 

淘宝最活跃开源项目：tengine \ tsar 
 
> git reset —head <commitID>   将git的指针head指向指定的CommitID实现代码的回退reset
> git reflog   查看reset之前的指针指向的commitID及操作命令
gitolite-mirror 
-------------------------------------------------------------------------------------------------------------------------------------------------
git中版本标识：
        HEAD  -- 表示当前最新版本，
        HEAD^  -- 表示上一个版本
        HEAD^^  -- 上上一个版本
        HEAD~100 --  往上数100个版本
     git reflog :  需要重返未来时，使用该命令查看命令历史，以便回到未来的某个版本
 
Git补丁管理

git diff > ../sync.patch         # 生成补丁
git apply ../sync.patch          # 打补丁
git apply --check ../sync.patch  # 测试补丁能否成功
git format-patch -X              # 根据提交的log生成patch，X为数字，表示最近的几个日志

 



 


git 怎么恢复到之前的版本？
2、gerrit代码审查网页工具

---------------------------   git 导出  ----------------------------------------------------------------
从 git 仓库中导出项目
git archive  --format  tar  --output  /path /to /file.tar master  # 将 master 以 tar 格式打包到指定文件


词汇：
* codeshelver
* GitHire


git关联远程分支：git branch --set-upstream production origin/production 

清理远程不存在的分支：
     git fetch  -p   或  git remote prune origin
git hooks 工具
工具 fabric
Slack 作为消息枢纽

Saltstack

git staging
git gc
git fsck
     git grep "key word"
 在某一版本中搜索文本
     git grep "key word" v2.5


将当前HEAD版本重置到分支中:





相同分支开发，别git pull代码，使用：git rebase 远程分支 (保证自己的提交不是合并，而是顺序的)


 








查看git@github.com:iballad/server-api.git  master分之源码



 