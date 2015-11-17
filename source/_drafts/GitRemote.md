title: "GitRemote"
date: 2015-11-17 15:08:24
categories: git
tags:
  - git
  - remote
---

  git remote set-url origin <url>     # 设置远程仓库地址（用于修改远程仓库的url ）

     git remote rm <repository-name>      # 删除远程仓库引用

     git remote set-head origin <branch-name>      # 设置远程仓库的HEAD指向 branch-name 分支

     查看远程仓库：git remote -v      (进入clone下的工程目录)
     添加远程 Git 服务器: git remote add origin https://github.com/verphen/test.git ( 即就是：git remote add [remote name] [url] )

     git remote show origin 查看远程关联


-----------------------------------------------------------------------------------------------------

提交本地code到远程服务器（GitHub）：
          git  remote  add origin  git@github.com:verphen/test.git  

     Git移除文件就必须要从已跟踪文件清单中移除（确切地说，是从暂存区域移除），然后提交。


http://www.yiibai.com/git/git_remote_operate.html

查看远程仓库信息：
     git remote -v
     git remote show origin

清理远程存在过但现在不存在的本地分支：git remote prune


git clone <url> [project_name]      # 从现有仓库中克隆

git remote                          # 查看所有远程仓库
git remote -v                       # 查看所有远程仓库的详细信息
git remote show <remote_name>       # 查看指定远程仓库

git remote add <remote_name> <url>      # 添加远程仓库
git remote set-url <remote_name> <url>  # 设置远程仓库地址
git remote rm <remote_name>             # 删除远程仓库
git remote rename <remote_name_old> <remote_name_new>       # 更名远程仓库


