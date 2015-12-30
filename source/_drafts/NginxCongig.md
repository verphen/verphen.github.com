title: Nginx 配置
date: 2015-11-22 18:08:00
categories: tools
tags:
  - nginx
  - tools
---

	$ nginx -t  # 检测配置文件是否正确

	$ nginx -s reload  	# 重载nginx配置

	$ nginx -c /usr/local/nginx/conf/nginx.conf    # 加载指定的配置文件启动

	$ user www-data; 	# 配置运行nginx的用户和用户组

	$ worker_processes 8; # 定义nginx进程数，建议设置为等于CPU总核心数


	全局错误日志定义类型，[ debug | info | notice | warn | error | crit ]用error_log指令。另外日志还可以定义在http、server及location上下文中，语法格式一样。

	error_log /var/log/nginx/error.log info;

http段的配置：

	


	设定虚拟主机用指令server，其中包括端口，主机名称，默认请求等设置。
	server {
	    #侦听80端口
	    listen       80;
	    #定义使用www.xx.com访问
	    server_name  www.xx.com;
	    #设定本虚拟主机的访问日志
	    access_log  logs/www.xx.com.access.log  main;
	    #默认请求
	    location / {
	          root   /root;      #定义服务器的默认网站根目录位置
	          index index.php index.html index.htm;   #定义首页索引文件的名称
	          fastcgi_pass  www.xx.com;
	          fastcgi_param SCRIPT_FILENAME $document_root/$fastcgi_script_name;
	          include /etc/nginx/fastcgi_params;
	     }
	 
	    # 定义错误提示页面
	    error_page   500 502 503 504 /50x.html; 
	    location = /50x.html {
	    root   /root;
	    }
	}
	请求转向指令proxy_pass

	proxy_pass http://www.hubwiz.com;




	负载均衡
		设定负载均衡的服务器列表用指令upstream。
		upstream mysvr {
			ip_hash;
		    #weigth参数表示权值，权值越高被分配到的几率越大
		    #本机上的Squid开启3128端口
		    server 192.168.8.1:3128 weight=5;
		    server 192.168.8.2:80  weight=1;
		    server 192.168.8.3:80  weight=6;
		}

		nginx的upstream目前支持4种方式的分配

	　　1)、轮询（默认） 每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除。

	　　2)、weight 指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。

	　　3)、ip_hash 每个请求按访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，可以解决session的问题。

	　　4)、fair（第三方） 按后端服务器的响应时间来分配请求，响应时间短的优先分配。




	location的匹配规则location [=|~|~*|^~] /uri/ { … }


	Nginx Rewrite 规则

		正则表达式匹配，其中：

		~ 为区分大小写匹配；
		~* 为不区分大小写匹配；
		!~和!~*分别为区分大小写不匹配及不区分大小写不匹配。
		文件及目录匹配，其中：

		-f和!-f用来判断是否存在文件；
		-d和!-d用来判断是否存在目录；
		-e和!-e用来判断是否存在文件或目录；
		-x和!-x用来判断文件是否可执行。
		flag标记有：

		last 相当于Apache里的[L]标记，表示完成rewrite；
		break 终止匹配, 不再匹配后面的规则；
		redirect 返回302临时重定向 地址栏会显示跳转后的地址；
		permanent 返回301永久重定向 地址栏会显示跳转后的地址。
		当然除了这些以外，Rewrite规则中还会用到一些相应的全局变量，如$args，$url等等


http://www.cnblogs.com/skynet/p/4146083.html


