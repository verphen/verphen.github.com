title: LinuxErrorAnalyse
tags:
---
在使用linux时，难免遇到各种异常错误；下面针对常出现的错误做简单的分析和解答(操作环境为centos，其他linux环境大同小异)

。sudo执行命令出现错误: `*** is not in the sudoers file. This incident will be reported`(***为你当前使用的用户名)

> 出现这个错误是因为该用户没有加入到sudo的配置文件，将该用户加入即可

$ su      # 切换至root用户
$ visudo      # 编辑sudo配置文件/etc/sudoers(即等同命令vi /etc/sudoers)加入内容
      # 在 `root    ALL=(ALL)       ALL`行后加入当前用户(***)配置，保存退出
      ***    ALL=(ALL)       ALL

。-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): 没有那个文件或目录

