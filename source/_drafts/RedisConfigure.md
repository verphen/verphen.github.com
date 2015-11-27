title: RedisConfigure
tags:
---

edis-server：Redis服务器的daemon启动程序
redis-cli：Redis命令行操作工具。当然，你也可以用telnet根据其纯文本协议来操作
redis-benchmark：Redis性能测试工具，测试Redis在你的系统及你的配置下的读写性能
redis-stat：Redis状态检测工具，可以检测Redis当前状态参数及延迟状况 

$redis-cli -p 6380 shutdown 关闭指定端口redis

redis-cli下命令：
	shutdown: 关闭redis服务


配置redis根目录下的redis.conf文件，修改redis.conf文件需要重启redis

	port: 配置redis访问端口（默认6379）

	daemonize: yes/no;是否后台启动

	requirepass: 设置密码
	不重启redis配置密码
		1. 修改redis.conf文件requirepass
		2. 进入redis-cli; 输入命令config get requirepass,得到如下显示
			1）“requirepasss”
			2) (null)
			显示密码为空，设置密码
		3. config set requirepass password 设置密码
		4. 查询密码: config get requirepass
		   显示结果： (error) ERR operation not permitted,需要登录
		5. auth password; 登录
		6. 再次查询密码： config get requirepass
		   显示结果：
		   	1）“requirepasss”
			2) "password"
		   密码修改成功

启动redis-cli时输入密码： reids-cli -a password
启动redis-cli之后输入密码：auth password

master 有密码,slave的配置：
	当master 有密码的时候配置slave 的时候 相应的密码参数也得相应的配置好。不然slave 是无法进行正常复制的。
	相应的参数是：
		#masterauth
		比如:
		masterauth  mstpassword

redis命令info:
	redis_version:2.4.16                                  # Redis 的版本
	redis_git_sha1:00000000
	redis_git_dirty:0
	arch_bits:64
	multiplexing_api:epoll
	gcc_version:4.1.2                                         #gcc版本号
	process_id:10629                                        # 当前 Redis 服务器进程id
	uptime_in_seconds:145830                      # 运行时间(秒)
	uptime_in_days:1                                        # 运行时间(天)
	lru_clock:947459                                        
	used_cpu_sys:0.02
	used_cpu_user:0.02
	used_cpu_sys_children:0.00
	used_cpu_user_children:0.00
	connected_clients:1                                  # 连接的客户端数量
	connected_slaves:0                                  # slave的数量
	client_longest_output_list:0
	client_biggest_input_buf:0
	blocked_clients:0
	used_memory:832784                               # Redis 分配的内存总量
	used_memory_human:813.27K
	used_memory_rss:1896448                     # Redis 分配的内存总量(包括内存碎片)
	used_memory_peak:832760                
	used_memory_peak_human:813.24K    #Redis所用内存的高峰值
	mem_fragmentation_ratio:2.28                 # 内存碎片比率
	mem_allocator:jemalloc-3.0.0                 

	loading:0
	aof_enabled:0                                                  #redis是否开启了aof
	changes_since_last_save:0                         # 上次保存数据库之后，执行命令的次数
	bgsave_in_progress:0                                   # 后台进行中的 save 操作的数量
	last_save_time:1351506041                        # 最后一次成功保存的时间点，以 UNIX 时间戳格式显示
	bgrewriteaof_in_progress:0                         # 后台进行中的 aof 文件修改操作的数量
	total_connections_received:1                      # 运行以来连接过的客户端的总数量
	total_commands_processed:1                    # 运行以来执行过的命令的总数量
	expired_keys:0                                                # 运行以来过期的 key 的数量
	evicted_keys:0                                                #运行以来删除过的key的数量
	keyspace_hits:0                                            # 命中 key 的次数
	keyspace_misses:0                                     # 不命中 key 的次数
	pubsub_channels:0                                     # 当前使用中的频道数量
	pubsub_patterns:0                                      # 当前使用的模式的数量
	latest_fork_usec:0                                      
	vm_enabled:0                                                # 是否开启了 vm (1开启  0不开启)
	role:master                                                     #当前实例的角色master还是slave
	db0:keys=183,expires=0                             # 各个数据库的 key 的数量，以及带有生存期的 key 的数量   










redis-cli下命令：

	$ keys '*'   # 列出redis中所有KEY


