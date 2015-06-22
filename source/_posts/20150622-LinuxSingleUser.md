title: linux单用户模式
tags:
  - linux
  - inittab
categories: linux
date: 2015-06-22 01:16:28
---
linux单用户模式使用场景：

- 忘记所有密码
- 错误的修改/etc/inittab文件，导致系统reboot重启不起来
- 安装没有图形界面的linux（centos-minimal）,而系统默认图形界面启动

进入单用户模式：

- grub启动时，按e键；然后利用键盘上下键，将光标定位到

		kernel /boot/vmlinuz-2.6.11-1.1369_FC4 ro root=LABEL=/1 rhgb quiet

- 再按一下e键，进入编辑这行，然后在行尾输入: linux single

		kernel /boot/vmlinuz-2.6.11-1.1369_FC4 ro root=LABEL=/1 rhgb quiet linux single

- 按回车结束编辑并返回

- 按一下b键重新启动，进入系统进行相关操作

<!-- more -->

如开篇的问题，修改新密码或者修改文件：

- 修改密码

		$ passwd username	# 输入新密码即可

- 修改默认启动模式（图形界面、命令行等）

		$ vi /etc/inittab 	# 图形界面（id:3:initdefault:），命令行（id:5:initdefault:）

	参考如图 <img src="/imgs/linux/inittab.png" alt="linux默认启动模式控制文件" />