title: "Logstash"
date: 2015-11-17 17:10:06
categories: toosl
tags:
  - log
  - logstash
---

centos安装logstash前提必须安装jdk（版本必须在1.7之上）

[官方文档](https://www.elastic.co/guide/en/logstash/current/package-repositories.html#_apt)

安装方式1：

执行命令
	
	$ rpm --import https://packages.elastic.co/GPG-KEY-elasticsearch

然后在目录 /etc/yum.repos.d/ 创建 .repo后缀文件，如logstash.repo,文件内容：

	[logstash-2.0]
	name=Logstash repository for 2.0.x packages
	baseurl=http://packages.elastic.co/logstash/2.0/centos
	gpgcheck=1
	gpgkey=http://packages.elastic.co/GPG-KEY-elasticsearch
	enabled=1

准备号之后，开始安装

	$ yun install logstash


安装方式2：
	
直接下载logstash二进制文件解压即可， 下载地址： https://www.elastic.co/downloads/logstash


[简单粗暴测试](https://www.elastic.co/guide/en/logstash/current/first-event.html)：

	$ cd logstash-{logstash_version}
	$ bin/logstash -e 'input { stdin { } } output { stdout {} }'

输入: hello word !
2013-11-21T01:22:14.405+0000 0.0.0.0 hello world

结束: ctrl + D
