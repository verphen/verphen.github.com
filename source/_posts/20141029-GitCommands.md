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