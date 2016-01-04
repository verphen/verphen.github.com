title: 将nginx制作为系统服务
tags:
---

新建nginx文件,添加内容：

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
	cp ./nginx  /usr/rc.d/init.d 	

	chmod +x /etc/rc.d/init.d/nginx # 设置文件可执行权限
	chkconfig --add nginx  # 添加至系统服务