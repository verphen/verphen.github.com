title: nginx加入系统服务
tags:
  - nginx
  - tools
categories: tools
date: 2016-01-04 22:08:00
---
将nginx加入系统服务，可用很方便的对nginx进行启动和停止等操作；本环境nginx安装在/usr/local/nginx目录，若你未安装在该目录需修改下面的shell脚本 ` DAEMON=/usr/local/nginx/sbin/$NAME ` 语句，指定nginx的安装目录。

新建nginx文件,添加内容(为方便显示对内容进行了缩进，你可以使用shift+tab来取消缩进至文件顶格)：

<!-- more -->

	#! /bin/bash
	# chkconfig: 35 85 15  
	# description: Nginx is an HTTP(S) server, HTTP(S) reverse
	set -e
	PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
	DESC="nginx daemon"
	NAME=nginx
	DAEMON=/usr/local/nginx/sbin/$NAME
	SCRIPTNAME=/etc/init.d/$NAME
	test -x $DAEMON || exit 0
	d_start(){
	    $DAEMON || echo -n " already running"
	}
	d_stop() {
	    $DAEMON -s quit || echo -n " not running"
	}
	d_reload() {
	    $DAEMON -s reload || echo -n " counld not reload"
	}
	case "$1" in
	start)
	    echo -n "Starting $DESC:$NAME"
	    d_start
	    echo "."
	;;
	stop)
	    echo -n "Stopping $DESC:$NAME"
	    d_stop
	    echo "."
	;;
	reload)
	    echo -n "Reloading $DESC configuration..."
	    d_reload
	    echo "reloaded."
	;;
	restart)
	    echo -n "Restarting $DESC: $NAME"
	    d_stop
	    sleep 2
	    d_start
	    echo "."
	;;
	*)
	    echo "Usage: $SCRIPTNAME {start|stop|restart|reload}" >&2
	    exit 3
	;;
	esac
	exit 0

然后执行以下命令：

	# 复制shell脚本nginx文件到目录/etc/rc.d/init.d/中
	cp ./nginx  /etc/rc.d/init.d 	

	chmod +x  /etc/rc.d/init.d/nginx 	# 设置文件可执行权限
	chkconfig --add nginx  	# 添加至系统服务

任何目录执行命令即可操作nginx：
	
	service nginx <start | stop | restart | reload > 	# <启动|停止|重启|重载> nginx