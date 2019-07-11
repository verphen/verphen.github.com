title: Upsource安装及配置
date: 2016-04-07 16:10:54
categories: git
tags: [upsource,git,code]
---

[Upsource](https://www.jetbrains.com/upsource/) 是jetbrains推出的代码审查code review工具，官方提出的口号"Polyglot code review tool" 通晓多种语言的代码审查工具；

<img src="/imgs/article/upsource.png" alt="upsource" />

### 下载

	直接官网download即可


### 安装

官网下载的文件一般为upsource-xxx.zip(作者下载版本upsource-3.0.4237.zip)，解压该文件到目录 /usr/local

	$ unzip upsource-3.0.4237.zip 		# 解压
	$ mv Upsource upsource 		# 改名
	$ mv Upsource /usr/local 		# 移动

### 配置
	
	. 将upsource启动命令加入系统环境变量便于启动; 将如下内容追加到/etc/profile文件尾部

		# config upsource env
		PATH=$PATH:/usr/local/upsource/bin

	$ source /etc/profile  		# 使环境变量生效, 免于重启系统

	$ upsource.sh <start|stop> 	$ [启动|停止] upsource


