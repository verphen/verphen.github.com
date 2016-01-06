title: nginx commands
tags:
  - nginx
  - tools
categories: tools
date: 2016-01-06 18:08:00
---

nginx帮助信息如其本身性能一样轻巧清晰简明，无需更多的额外说明； 使用 `nginx -?` 到的帮助信息:

	nginx version: nginx/1.8.0
	Usage: nginx [-?hvVtq] [-s signal] [-c filename] [-p prefix] [-g directives]

	Options:
	  -?,-h         :  this help
	  -v            :  show version and exit
	  -V            :  show version and configure options then exit
	  -t            :  test configuration and exit
	  -q            :  suppress non-error messages during configuration testing
	  -s signal     :  send signal to a master process: stop, quit, reopen, reload
	  -p prefix     :  set prefix path (default: /usr/local/nginx/)
	  -c filename   :  set configuration file (default: conf/nginx.conf)
	  -g directives :  set global directives out of configuration file