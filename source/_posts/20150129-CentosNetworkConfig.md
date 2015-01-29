title: CentOS Network Config
date: 2015-01-29 23:37:34
categories: linux
tags: [linux,centos]
---
前些日子安装了CentOS minimal版本的操作系统虚拟机（当然实体机安装也大同小异），这个版本应该是CentOS发行版本中集成软件和环境的最少的，方便学习建议安装此版本从零开始。安装之后发现无法上网，于是开始探索查询.

怎么检测是否可用联网？使用 `ping www.baidu.com `命令查看发包和接受包的状况（俗话说是否可用'ping通'）,当然你可以使用浏览器测试进行测试；如发现无法解析主机等提示之类的提示说明无法联网，则开始配置 centos 的网络配置文件 `/etc/sysconfig/network-scripts/ifcfg-eth*`; ifcfg-eth*文件的数量表示你机器网卡的数量，如只有一块网卡则在目录 ` /etc/sysconfig/network-scripts/ ` 下只会存在一个ifcfg-eth*文件（那就是ifcfg-eth0）,文件结构（参数配置）如下：
          	
	DEVICE="eth0"				  //指出设备名称
	BOOTPROTO="dhcp"			  //启动类型 dhcp
	HWADDR="00:0C:29:35:A2:A8"	  //硬件Mac地址
	IPV6INIT="yes"				  //是否支持IPV6
	NM_CONTROLLED="yes"			  //network manger参数，修改实时生效无需重启网卡
	ONBOOT="yes"			 	  //是否启动应用
	TYPE="Ethernet"				  //网络类型
	UUID="733r86e3-a47e-4471-a83f-1ef4def437bb"

然后保存并退出， 重启网络服务：` service network restart `即可;我无法联网的问题是参数ONBOOT="no"的原因造成。
