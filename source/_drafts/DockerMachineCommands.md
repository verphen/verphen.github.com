title: DockerMachineCommands
tags:
---

$ docker-machine ssh default	# 连接docker默认虚拟机(用户名docker / 密码tcuser)
     

属性docker-machine命令
     docker-machine ls      # 列出所有docker machine
     docker-machine create - - driver virtualbox default      # 创建新的docker虚拟机;
     docker-machine env default      # 获取虚拟机default的环境变量
     eval $(docker-machine env default)     # 连接到default虚拟机
     docker-machine rm <machine-name>     # 删除某台虚拟机
     docker-machine start <machine-name>     # 启动虚拟机
      $ docker-machine restart default      #  重启docker虚拟机default

 

本机无法登录或者pull docker私有库；需要修改docker创建的默认虚拟机default:

	$ docker-machine ssh  default

	$ cd   /var/lib/boot2docker

	$ vi profile	# 内容显示如下


		EXTRA_ARGS='
		--label provider=virtualbox
		--insecure-registry harbor.product.co-mall
		'
		CACERT=/var/lib/boot2docker/ca.pem
		DOCKER_HOST='-H tcp://0.0.0.0:2376'
		DOCKER_STORAGE=aufs
		DOCKER_TLS=auto
		SERVERKEY=/var/lib/boot2docker/server-key.pem
		SERVERCERT=/var/lib/boot2docker/server.pem

在--label provider=virtualbox 下一行追加内容：	“--insecure-registry harbor.product.co-mall”,  重启docker即可


# config JVM timeZone to GMT+08
JAVA_OPTS=%JAVA_OPTS% -Duser.timezone=Asia/Shanghai



调试问题:

	cd /sources/eclipse/cybershop-rest-api

	# 构建docker镜像
	docker build -t mytest .

	# 启动镜像
	docker run -it mytest /bin/bash



dockerfile 命令 ENTRYPOINT是什么意思

