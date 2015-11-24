---
title: Git的安装及使用
date: 2012-12-04 15:40:32
categories: tools
tags: [git,工具]
---
Git是一个分布式管理工具，通过字符串来时刻保持数据的完整性，关心的是文件数据整体的变化，并不保存变化前后的差异数据；Git 在本地磁盘保存有关项目的历史更新，所有绝大多数操作只需要访问本地文件资源，并不需要Internet。当然可以使用GitHbub将代码托管，进行远程开发，方便团队比较分散的情况（这正体现Git分布式的优势）；开发人员只需将项目clone到本地，进行相应的开发然后push上传到GitHub（GitHub使用的是utf-8编码，所以上传的文件如若不是以utf-8编码，可能出现乱码），供别的开发人员更新即可。

<!-- more -->

### 下载安装 ###

Git在windows的版本是[msysgit](http://git-scm.com/download),或者在google code[下载](http://code.google.com/p/msysgit/downloads/list);下载完成自行安装,很简单的(如果你需要在windows控制台使用git命令，你必须把git安装路径的bin目录加入到环境变量)；Git安装完成应该有Git Bash和Git Gui（可视化操作），建议使用Git Bash，理解git的命令操作（Linux下的大部分名字在git bash下都能使用）；


任何文件在Git库中都有四种状态：未跟踪状态untracked、跟踪状态tracked（未修改状态unmodified、已修改状态modified、暂存状态staged），由于文件的上述四种状态，在使用Git进行项目管理的时候涉及到三个区域：

-  Git 本地数据目录：每个项目都有一个 git 目录，它是 Git 用来保存元数据和对象数据库的地方。该目录非常重要，每次克隆镜像仓库的时候，实际拷贝的就是这个目录里面的数据。
-  工作目录（项目工作空间）：从项目中取出某个版本的所有文件和目录，用以开始后续工作的叫做工作目录，即就是我们进行项目开发的目录。
-  暂存区域：所谓的暂存区域只不过是个简单的文件，一般都放在 git 目录中。

git经常使用的命令

1.  Git本地仓库的基本用法：
	-  git init ：初试化当前目录为一个Git本地仓库。
	-  git add <filename> : 如果一个文件是未被跟踪的，将 一个文件加入到Git版本控制当中，让Git对其进行跟踪；如果一个文件是已修改状态，则将一个文件放到暂存区中。
	-  git add .  :  "."点表示当前目录下的所有内容
	-  git status : 查看当前Git仓库中所有文件的状态，若是为跟踪状态 则用红色显示。
	-  git diff：比较工作目录中当前文件和暂存区域快照之间的差异，也就是修改之后还没有暂存起来的变化内容。
	-  git commit：提交暂存区域。git commit -m <说明信息>;git commit -a 可以跳过暂存区域，直接将已跟踪的文件暂存起来一并提交。
	-  git rm <filename>：从Git中删除一个文件。git rm --cached <filenmae>：从暂存区删除一个文件，但是仍保留在工作目录中。也就是将文件变为未跟踪状态。
	-  git log：查看项目提交历史记录。
		-  git log -p 选项展开显示每次提交的内容差异
  		-  git log --stat 仅显示简要的增改行数统计
 		-  git log --pretty=<option> ，其中option可以是：oneline（使每条历史信息在一行中显示），short，full，fuller，format（按指定的格式输出）
               gitk 可以打开历史记录的可视化查看窗口。
	-  git commit --amend：修改最后一次提交。该命令是提交当前缓存区快照，并修改最后一次的说明。
	-  git checkout -- <filename>：撤销对文件的修改，慎用！   
	-  git reset HEAD <filename>：撤销对文件的暂存，让文件回到暂存前的状态。 
-  Git远程仓库的基本用法：
	-  git clone [url]：将一个远程仓库克隆到本地。
	-  git remote：查看当前配置的远程仓库，在克隆完某个项目后，至少可以看到一个名为origin的远程仓库，Git 默认使用这个名字来标识你所克隆的原始仓库。如git remote add origingit@github.com:usernmae/repositoryname.git
		-  -v ：显示对应的克隆地址。
		-  git remote add [remote-name] [url]：添加一个新的远程仓库。
		-  git remote show [remote-name]：查看远程仓库信息。
		-  git remote rm [remote-name]：移除远程仓库。
		-  git remote rename [old-remote-name] [new-remote-name]：重命名远程仓库。
	-  git push [remote-name] [branch-name]：推送数据到远程仓库，remote-name指的是远程仓库简称，branch-name指的是分支名称。对于克隆的仓库默认分别为：origin，master;git push -u origin master //将本地的项目提交到远程仓库
-  Git将远程仓库GitHub取回本地：

	-  git [url]: 在git下切换到想要存放此项目的目录，运行这条命令就可以将项目克隆到本地磁盘的当前目录
	-  项目取回本地，远程仓库GitHub上有更新;`git fetch origin`开始取得更新;`git merge origin /master`将更新内容合并到本地分支/master

系统的学习Git可以参考：<a href="http://gitref.cyj.me/zh/index.html">《Git参考手册》</a>、<a href="http://gitref.cyj.me/">英文版《Git参考手册》</a>、<a href="http://git-scm.com/book/zh/ ">官方Book《Pro Git》</a>、<a href="http://git-scm.com/book">英文版《Pro Git》参考</a>