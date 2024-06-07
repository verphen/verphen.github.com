title: IDEA plugin study note
date: 2024-04-24 14:42:59
updated: 2024-04-24 14:42:59
categories: IDEA
tags: IDEA插件
---

Gradle项目编译IDEA插件步骤：
1. Gradle项目管理面板 -> 项目 -> Tasks -> intelliJ -> buildPlugin -> 双击
2. 编译之后的插件文件目录：项目更目录 -> build -> distributions -> 插件文件.zip




异常记录：
1. System.out.println()打印中文乱码；启动项目时提示“The IDE is not configured for using custom VM options (jb.vmOptionsFile=null)”
	
	解决方法： IDEA工具栏 -> help -> Edit Custom VM Options... ， 添加“-Dfile.encoding=UTF-8”保存，重启IDEA即可