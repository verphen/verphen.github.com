title: Git Config
date: 2015-11-10 18:17:52
categories: git
tags:
  - config
  - git
---

git config --global user.name "username"     设置全局用户名     用户名和邮箱用于提交日志的描述
     git config --global user.email "user@xxx.com"     设置全局邮箱
     git config --global color.ui [true|false]   git会显示适当地颜色[打开|关闭]     
     
git config --global alias.st status : 修改status为别名st (一般常用commit-ci, checkout--co, branch--br)     

               --global 是全局参数，也就是这些命令在这台电脑的所有git仓库都有用 ( 加上该参数配置后存储文件: 用户目录/.gitconfig ; 没有该参数则存储文件: 项目/.git/config )

     git config --list    列出所有配置(可以使用grep过滤)   --同命令： git config -l

     git config --global --unset alias.st   取消全局别名设置(删除对应文件的的字段同样可以实现)
