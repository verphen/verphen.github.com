
redis 监控：

	# 100个并发连接，100000个请求，检测host为localhost 端口为6379的redis服务器性能 
	$ redis-benchmark -h localhost -p 6379 -c 100 -n 100000 -a admin


	# 监控host为localhost，端口为6380，redis的连接及读写操作 
	$ redis-cli -h localhost -p 6380 monitor 



