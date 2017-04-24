title: Docker 命令
tags:
---
docker上传镜像只docker hub:
    # 登录docker hub
    $ docker login [OPTIONS] [SERVER]
    Options:
	      --help              Print usage
	  -p, --password string   Password
	  -u, --username string   Username
    $ docker login -u=<name> -p=<passwd>
    
    # 制作tag
    $ docker tag <imageID> <namespace>/<imageName>:<version>
    
    # push镜像至docker hub
    $ docker push <namespace>/<imageName>

注： 以下命令出现的COTAINER可以用容器名或容器ID来使用





$ docker version 	# 查看docker Client及Server版本信息
$ Docker info	# 查看系统范围信息


$ docker images [OPTIONS] [REPOSITORY[:TAG]]	# 查看本机的所有镜像
$ docker search [OPTIONS] TERM 		# 搜索镜像(默认官网搜索)
$ docker pull [OPTIONS] NAME[:TAG|@DIGEST] 	# 默认从官方(dockerhub.com)拉取镜像
$ docker rmi [OPTIONS] IMAGE [IMAGE...] 	# 删除镜像

$ docker history [OPTIONS] IMAGE 	# 显示镜像历史
OPTIONS选项：
	-H, --human=true    以可读格式打印大小及日期
	--help              Print usage
	--no-trunc          显示完整的提交记录，不截断输出
	-q, --quiet         仅列出提交记录ID


# 启动容器
$ docker run [OPTIONS] IMAGE[:TAG] [COMMAND] [ARG...]
eg: docker run -it --name <name> -p <port:port> -v <dir:dir>  <image>  # 常用参数

OPTIONS选项:
	-i, --interactive 		Keep STDIN open even if not attached
	-t, --tty               Allocate a pseudo-TTY
	-p, --publish=[]        指定宿主机端口到容器端口的映射(多个端口映射用顿号分隔)
	-d, --detach			在后台运行容器，并打印容器ID
	-v, --volume=[]			绑定数据卷，若在容器目录后加":ro"表示创建的数据卷为只读(eg: docker run -v <宿主机目录:容器目录:ro> image)
	--name					给容器分配一个名字


# 显示容器列表
$ docker ps [OPTIONS]

OPTIONS选项：
	-a, --all 		显示所有运行及停止的容器（不加该选项只显示正在运行的容器）



# 保存对容器的修改（在容器中执行命令或安装软件后，通过该命令固化新镜像，下次即可使用最新状态的镜像）
$ docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]









# 移除一个或多个容器
$ docker rm [OPTIONS] CONTAINER [CONTAINER...]

OPTIONS选项：
	-f, --force 	强制移除容器(即使容器还在运行)
	-l, --link		移除容器间的网络连接，而非容器本身
	-v, --volumes	移除与容器关联的空间
	--help 			Print usage

eg: docker rm -f $(docker ps -a -q)   	# 删除所有容器（包括运行中的容器）


# 重命名容器
$ docker rename [OPTIONS] OLD_NAME NEW_NAME




# 停止容器
$ docker stop [OPTIONS] CONTAINER [CONTAINER...]
OPTIONS选项：
	-t, --time=10 	 指定时间后停止容器

# 启动容器
docker start [OPTIONS] CONTAINER [CONTAINER...]
Options:
	-a, --attach               Attach STDOUT/STDERR and forward signals
      --detach-keys string   Override the key sequence for detaching a container
      --help                 Print usage
	-i, --interactive          Attach container's STDIN


# 杀死容器(被杀的容器必须运行，且docker ps -a不会显示)
$ docker kill [OPTIONS] CONTAINER [CONTAINER...]
Options:
      --help            Print usage
  -s, --signal string   Signal to send to the container (default "KILL")




# 以dockerfile创建镜像
$ docker build [OPTIONS] PATH | URL | -			
# eg: docker build -t <IMAGE_NAME> <Dockerfile_path>
OPTIONS选项：
	-t, --tag=[] 	 指定镜像名字及可选的TAG，格式为'IMAGE_NAME:TAG'

# 給镜像打标签
$ docker tag [OPTIONS] IMAGE[:TAG] [REGISTRYHOST/][USERNAME/]NAME[:TAG]


# 查看容器端口映射列表
$ docker port [OPTIONS] CONTAINER [PRIVATE_PORT[/PROTO]]
eg: docker port tomcat		# 查看容器tomcat的端口映射情况

# 退出容器
$ exit 		交互方式启动的容器可以使用ctrl + c 退出容器
 
# 查看容器或镜像基本的信息
$ docker inspect [OPTIONS] CONTAINER|IMAGE [CONTAINER|IMAGE...]
OPTIONS选项：
	-f, --format       指定给定的如果Go语言模板
  	--help             Print usage
  	-s, --size         如果是容器，显示总文件大小
  	--type             返回JSON的特定类型（类型为container或image）

# 连接到运行的容器
$ docker attach [OPTIONS] CONTAINER
OPTIONS选项：
	--detach-keys       Override the key sequence for detaching a container
  	--help              Print usage
  	--no-stdin          Do not attach STDIN
  	--sig-proxy=true    Proxy all received signals to the process

  
# 保存镜像
$ docker save [OPTIONS] IMAGE [IMAGE...]
eg: docker save image_name > /home/save.tar
Options:
  -o, --output string   Write to a file, instead of STDOUT

# 加载镜像
docker load [OPTIONS]
Options:
  -i, --input string   Read from tar archive file, instead of STDIN
  -q, --quiet          Suppress the load output


技巧：

	。 由于某些原因，pull Docker镜像比较慢，你可以使用Daocloud的Docker加速器，https://www.daocloud.io/mirror#accelerator-doc

