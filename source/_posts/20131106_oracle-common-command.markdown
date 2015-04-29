---
title: Oracle common commands
date: 2013-11-06 22:58:46
categories: database
tags: [oracle,数据库]
---
冬天来了，开始进入工作的节奏做项目，项目使用Oracle数据库，由于之前学习使用过一段时间Oracle，现在补充一下Oracle方面的只是，便于熟悉记忆：

使用Oracle数据库需要理解的名词：用户、角色、表空间、权限，我在别人的电脑导出数据库dmp文件，然后在本机进行导入（我使用的win8系统，win+r进入运行，cmd进入dos）: 
`imp username/password@netname file=path\filename.dmp log=C:\log.log full=y`（只有管理员角色才有这样的权限 Only a DBA can import file exported by another DBA ），可以参考<a href="http://wenku.baidu.com/view/4ad1d162caaedd3383c4d35d.html">《dmp文件导入Oracle数据库》</a>这篇文件。

+ username：用户名
+ password：密码
+ netname：实例名称，即就是数据库
+ file：导入的dmp文件（完整路径）
+ log：导入过程中产生的日志保存在该文件
+ full：是否需要全部导入,只有当前用户是dba的时候，才能使用此项 

Oracle使用过程中接触到的一些常用操作及命令：

- 清屏（host cls、clear screen、cleascre），只要在sqlplus中命令前加上host就能使用windows本机的dos命令；
- 解锁scott用户：alter user scott account unlock；
- 修改密码：alter user scott identified by tiger;
- show user；查看当前用户
- disc 断开连接；conn 连接