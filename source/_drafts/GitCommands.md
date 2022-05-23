title: git 克隆
tags:
  - git
  - command
date: 2015-09-16 22:35:35
categories: git
---

	$ git help 		# Git帮助(常用的Git命令及描述)

	$ git help <command>    # 显示command命令的帮助

	$ git <command>  --help   # 以HTML显示command命令详细帮助(Launching default browser to display HTML ...)

    $ git show [commitID]   # 显示上一次提交详细差异信息[指定版本的差异信息]

    $ gitk  #  可视化界面查看提交记录等

克隆本地仓库： git clong /path/repository
克隆远程仓库： git clone username@hostname:/path/repository


git clone <url> [project_name]      # 从现有仓库中克隆

git reflog：查看上一次版本情况（回退也能看到）

git rebase master               # 将指定分支的超前提交变基到当前

git mv <file_old> <file_new>    # 重命名跟踪文件




  -  



git co  -- <file>   # 抛弃工作区修改
git co  .           # 抛弃工作区修改
git co HEAD <file>  # 抛弃工作目录区中文件的修改


$ git checkout .    # 丢弃当前目录(及所有子孙目录)所有文件在工作区的修改，即恢复到最近一次add或commit的状态（注意命令最后有一个点号"."）
$ git checkout filename   # 丢弃具体文件在工作区的修改



git add <file>      # 将工作文件修改提交到本地暂存区
git add .           # 将所有修改过的工作文件提交暂存区

git rm <file>       # 从版本库中删除文件
git rm <file> --cached  # 从版本库中删除文件，但不删除文件

 

git ci <file>
git ci .
git ci -a           # 将git add, git rm和git ci等操作都合并在一起做
git ci -am "some comments"
git ci --amend      # 修改最后一次提交记录


git add -p filename 实现多次提交

git status
git add .
git commit -m "commit info"
     git commit -a -m 'comment'  （git commit -am 'comment'）


git status          #查询当前文件状态

git add <file>      # 将目标文件快照放入暂存区，同时未被跟踪的文件标记为需要跟踪

git rm <file>               # 从暂存区域以及工作目录中移除指定文件。
git rm --cached <file>      # 从暂存区域中移除，但仍保留在工作目录，即从跟踪清单中删除。

git commit                      # 提交已暂存的文件
git commit -m "comment"         # 提交已暂存的文件，并填写备注
git commit -a -m "comment"      # 暂存并提交所有已跟踪过的文件
git commit --amend              # 撤销最后提交


#方式一
git add --all .
#方式二
git add -A .
  * –all 参数，顾名思义，添加所有文件（change|delete|add）
  * -A 参数，添加修改过和删除过的文件（change|delete）
  * 不加 参数，添加修改过和添加的文件（change|add）

git add -i，交互式的方式进行添加。
http://marklodato.github.io/visual-git-guide/index-zh-cn.html


git add -p filename 选择内容分步提交
     
  * 输入 y 来暂存该块

  * 输入 n 不暂存

  * 输入 e 手工编辑该块

  * 输入 d 退出或者转到下一个文件

  * 
输入 s 来分割该块





$ git add <resolved-file>
$ git rm <resolved-file>

git commit  --amend  -m  "commit message."  -m参数的意义


 跳过暂存区域进行commit : git commit -a -m "commit info"


提交，并将提交时间设置为之前的某个日期:
     git commit --date="`date --date='n day ago'`" -am "Commit Message"
     git commit --date "2015-06-13 11:21:32" -m "commit info"

git commit --amend ：修改上次提交(切勿修改已发布的提交记录)


git commit -a自动添加被修改文件（不包括新建文件）到索引，并自动提交



