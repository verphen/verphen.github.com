title: Git 提交记录
date: 2015-11-17 14:16:20
categories: git
tags:
  - git
  - log
---


git log git log <file> # 查看该文件每次提交记录 
git log -p <file> # 显示版本历史，以及版本间的内容差异 
git log -p -2 # 查看最近两次详细修改内容的diff 
git log --stat # 查看提交统计信息 
git log --since="6 hours" # 显示最近6小时提交 
git log --before="2 days" # 显示2天前提交 
git log -1 HEAD~3 # 显示比HEAD早3个提交的那个提交 
git log -1 HEAD^^^ git reflog # 查看操作记录


git log显示提交历史。练习其参数的使用
git log # 查阅提交历史 gitk # GUI方式查阅提交历史


git  log -p [filename] 显示文件提交日志信息和文件修改状态

在之前的教程中，我们了解了git log命令的用法，然而，它还有三个选项，你应该了解。

	* --oneline——把每次提交间显示的信息压缩成缩减的hash值和提交信息，在一行显示。
	* --graph——该选项会在输出界面的左手边用一种基于文本的图形表示法来显示历史。
如果你只是浏览一个单独分支的历史，那么这个功能是没有用的。
	* --all——显示全部分支的历史



 git log ：查看提交日志

  git log --pretty=oneline: 只显示commit id和提交信息 (查看- - pretty属性值)

    git log --graph: 查看分支合并图

git log -p master..origin/master     (查看本地分支和远程更新的差异)


git log --graph --decorate --pretty=oneline --abbrev-commit
    –graph 会在各个提交之间打印出线条，这些线条可以展示出分支之间的关系。
    –decorate 显示出分支处在哪一次提交上。
    –pretty=oneline 只是在一行中显示 sha1 和 提交的注释(译者将title一词应对到更精确的注释)
    –abbrev-commit 用开始的7个sha1字符代替整个sha1（他在你的仓库中是唯一的）



查看提交日志
git log  # 查看提交信息 
git log  --pretty=oneline  # 以整洁的单行形式显示提交信息



. git log --oneline     显示所有提交（仅显示提交的hash和message
  git log --author="username"   显示某个用户的提交

显示某个文件的所有修改：
$ git log -p <file>



git log [--all默认| --online压缩模式| --graph图形模式]



