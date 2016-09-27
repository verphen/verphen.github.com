
yum groupinstall 命令详解
yum groupinfo []

加密：
https://my.oschina.net/u/724133/blog/299362

yum  -y groupinstall  "Development Tools"


show variables like '%max_connections%';


zabbix安装教程：http://www.360doc.com/content/14/0529/21/8085797_382121204.shtml



GRANT ALL PRIVILEGES ON zabbix.* TO zabbix@localhost IDENTIFIED BY 'zabbix' WITH GRANT OPTION;



待完成：

	同步zabbix的服务器时间（Server  agent）






 http://blog.chinaunix.net/uid-10299986-id-2964493.html

yum -y install 包名（支持*） ：自动选择y，全自动
yum install 包名（支持*） ：手动选择y or n
yum remove 包名（不支持*）
rpm -ivh 包名（支持*）：安装rpm包
rpm -e 包名（不支持*）：卸载rpm包



docker 网络管理：
	docker network create --subnet=172.18.0.0/16 shadownet
	docker network create --subnet=10.0.110.0/24 oraclenet

	docker run --net shadownet --ip 172.18.0.22 --net oraclenet --ip 10.0.110.22 -it testimage /bin/bash
	运行后的容 器只加入到oraclenet里了。	 