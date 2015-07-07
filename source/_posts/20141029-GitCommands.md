title: Git Commands
date: 2014-10-30 07:44:00
categories: tools
tags: [tools,git]
---
简单描述Git常用命令，其都是在git bash中执行；linux大部分命令在git bash中都能使用（如ls、cat、vi ...）,但是也存在部分不能使用(如ll命令等),下面记录以下git特有的命令：

<p>常用命令

-  git init : 初始化项目；项目根目录下执行该命令,将该项目交给git工具进行管理，生成目录 .git
-  git clone url: 克隆远程项目，url为远程项目地址(github...)或者自搭建服务器地址;克隆时会将远程所有分支全部复制到本地
-  git status: 查看文件状态
-  git add filename: 使git开始跟踪该文件,此时该文件处于暂存状态
-  git commit -m "infomation": 提交文件至暂存区
-  git remote show origin: 查看远程关联

<!-- more -->

-  git rm filename --cached: 将文件（可以添加多个文件，多个文件用空格隔开）移除git管理
-  git rm -r directory-name --cached: 将目录（可以添加多个目录，多个目录用空格隔开）移除git的管理； -r表示目录级联（该目录及其所有子目录）

<p>分支管理

- git branch --help: 查看关于git branch帮助
- git branch [a|r...]: 查看本地分支(不带任何参数)，分支名前带星号" * "的是当前分支
	- -a: 查看所有(all)分支（本地及远程分支）
	- -r: 查看远程（remote）分支
	- -d branch-name: 删除(delete)本地分支(分支名：branch-name),该分支必须全部合并到不相关分支,没有未完成的操作
	- -D branch-name: 删除本地分支(分支名：branch-name),无论该分支是否合并到其他不相关分支
	- -r -d origin/remoe-branch-name: 删除远程分支(分支名：remote-branch-name)
	- git push origin :remote-branch-name: 删除远程分支(分支名：remote-branch-name),冒号前面的空格不能少;原理：把空分支push到远程server上,达到删除的结果
	- -m oldName  newName: 重命名(rename)move分支(待命名分支名：oldName;命名成分支：newName) 
- git branch branch-name: 创建分支（分支名:branch-name）