title: Git 远程
date: 2015-11-17 15:08:24
categories: git
tags:
  - git
  - remote
---

$ git remote        # 查看所有远程仓库别名
$ git remote -v     # 查看所有远程仓库别名及地址
$ git remote show <remote-name>    # 查看远程仓库地址及分支情况

$ git remote  add <remote-name>  <remote-url>   # 添加远程仓库别名及对应的远程地址 
  eg: git remote add origin git@github.com:effine/test.git

$ git remote set-url <remote-name> <url>  # 设置[更新]指定远程仓库名的地址
 
$ git remote rm <remote-name>     # 删除指定的远程仓库名
$ git remote rename <old> <new>       # 重命名远程仓库名



     git remote set-head origin <branch-name>      # 设置远程仓库的HEAD指向 branch-name 分支

http://www.yiibai.com/git/git_remote_operate.html

清理远程存在过但现在不存在的本地分支：git remote prune



usage: git remote [-v | --verbose]
   or: git remote add [-t <branch>] [-m <master>] [-f] [--tags | --no-tags] [--mirror=<fetch|push>] <name> <url>
   or: git remote rename <old> <new>
   or: git remote remove <name>
   or: git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
   or: git remote [-v | --verbose] show [-n] <name>
   or: git remote prune [-n | --dry-run] <name>
   or: git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)...]
   or: git remote set-branches [--add] <name> <branch>...
   or: git remote set-url [--push] <name> <newurl> [<oldurl>]
   or: git remote set-url --add <name> <newurl>
   or: git remote set-url --delete <name> <url>

    -v, --verbose         be verbose; must be placed before a subcommand



