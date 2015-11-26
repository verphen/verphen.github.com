title: SSH免密码登陆
date: 2015-05-20 17:11:02
categories: linux
tags:
  - linux
  - ssh
---

<img src="http://7xlmfk.com1.z0.glb.clouddn.com/imgs/linux/ssh.jpg" alt="SSH免密码登录" />

频繁操作多台linux服务器互相SSH访问，输入密码是个残酷的操作，当遇到密码复杂我就砸键盘砸屏幕，下月工资已预支；于是，开始实施SSH免密码登录。

<!-- more -->

本地通过SSH登录远程主机,首先需要在本地生成密钥：

	$ ssh-keygen [-t rsa]		# 本地主机生成密钥[采用rsa算法生成]

一直回车即可,最后将会在用户目录 ~/.ssh 生成公钥 id_rsa.pub 和私钥 id_rsa 两个文件,将公钥内容追加到远程主机文件 ~/.ssh/authorized_keys 文件中：
    
    $ ssh-copy-id [-i [identity_file]] [user@]machine   # 追加本机公钥到远程主机的authorized_keys

输入远程主机密码即完成配置；此时便可以实现SSH免密码登录远程主机。当然，追加公钥内容到主机时，你也可以上传公钥文件到远程主机，然后执行命令：

	$ cat <id_rsa.pub>  >>  ~/.ssh/authorized_keys		# 追加id_rsa.pub内容到authorized_keys文件内容尾部

我远程主机home目录存在本机公钥id_rsa.pub文件,所以我执行以下命令即可：

	$ cat /home/id_rsa.pub path   >>    ~/.ssh/authorized_keys

扩展阅读： google搜索ssh-keygen参数设置