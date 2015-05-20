title: Omit Passwd Login for SSH
date: 2015-05-20 17:11:02
categories: linux
tags:
  - linux
  - command
---

<img src="/imgs/linux/ssh.jpg" alt="SSH免密码登录" />

频繁操作多台linux服务器互相SSH访问，输入密码是个残酷的操作，当遇到密码复杂我就砸键盘砸屏幕，下月工资已预支；于是，开始实施SSH免密码登录。

<!-- more -->

本地主机(localHost)通过SSH登录远程主机(remoteHost),首先在localHost生成密钥：

	$ ssh-keygen		# 本地主机生成密钥
	等同于
	$ ssh-keygen -t rsa 	

一直回车即可,最后将会在目录 ` ~/.ssh ` 生成公钥id_rsa.pub和私钥id_rsa两个文件,将公钥内容追加到remoteHost服务器 ` ~/.ssh/authorized_keys`文件中

	$ ssh-copy-i ~/.ssh/id_rsa.pub <your-username>@remoteHost		# 追加本机公钥到remoteHost的authorized_keys

输入remoteHost密码即可实现SSH免密码登录远程主机

当然，追加localHost公钥内容到remoteHost文件authorized_keys时，你也可以上传localHost的公钥文件id_rsa.pub到remoteHost，然后执行命令：

	$ cat <id_rsa.pub path> >> ~/.ssh/authorized_keys		#追加id_rsa.pub内容到authorized_keys文件内容尾部

我的远程主机/home目录存在localHost的公钥id_rsa.pub,所以我执行以下命令即可：

	$ cat /home/id_rsa.pub path >> ~/.ssh/authorized_keys