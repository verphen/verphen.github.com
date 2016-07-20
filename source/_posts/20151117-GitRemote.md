title: 'Git Remote'
tags:
  - git
  - remote
categories: git
date: 2015-11-17 15:08:24
---
Git Remote命令官方解释是：管理和设置当前分支跟踪的仓库；原文`Manage the set of repositories ("remotes") whose branches you track.` 

    $ git remote        # 查看当前分支跟踪(远程)仓库别名(一般为origin，以下统一采用该别名)
    $ git remote <-v | --verbose>     # 查看跟踪仓库别名及地址
    $ git remote show <origin>    # 查看跟踪仓库地址及分支情况

    $ git remote add <origin> <url>   # 添加跟踪仓库别名及对应的跟踪地址 

    # 更新指定跟踪仓库名的地址
    $ git remote set-url [--push] <origin> <newurl> [<oldurl>] 
    $ git remote set-url --add <origin> <newurl>
    $ git remote set-url --delete <origin> <url>
        [--push]                # manipulate push URLs(操作push的URL)
        [--add]                # add URL
        [--delete]              # delete URLs

    $ git remote <remove|rm> <origin>     # 删除指定的跟踪仓库名
    $ git remote rename <old> <new>       # 重命名跟踪仓库名

    # 设置或删除跟踪仓库的HEAD指向指定分支,命令行中的圆括号表示必选其中之一执行
    $ git remote set-head <origin> (-a | --auto | -d | --delete | <branch>) 
        [-a|--auto]         # set refs/remotes/<name>/HEAD according to remote
        [-d|--delete]       # delete refs/remotes/<name>/HEAD

    # 清理存在过但现在不存在的本地跟踪分支的引用
    $ git remote prune [<options>] <origin> 
        [-n|--dry-run]         # dry run(试运行，彩排)