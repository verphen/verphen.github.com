title: Docker 命令
tags:
---

注： 以下命令出现的COTAINER可以用容器名或容器ID来使用

$ docker version 	# 查看docker版本信息
$ docker images 	# 查看本机的所有镜像
$ docker pull IMAGE 	# 默认从官方(docker.com)拉取镜像
ps: 若未翻墙，可以去国内镜像库(daocloud.io)查找对应镜像来拉取

# 启动容器
$ docker run [OPTIONS] IMAGE[:TAG] [COMMAND] [ARG...]
$ docker run  [-d] [-p external-ip:container-ip] [-i] [-t]  <REPOSITORY:TAG | IMAGE ID>

OPTIONS选项:
	-i, --interactive 		Keep STDIN open even if not attached
	-t, --tty               Allocate a pseudo-TTY
	-p, --publish=[]        指定宿主机端口到容器端口的映射(多个端口映射用顿号分隔)
	-d, --detach			在后台运行容器，并打印容器ID
	-v, --volume=[]			绑定数据卷，若在容器目录后加":ro"表示创建的数据卷为只读(eg: docker run -v <宿主机目录:容器目录:ro> image)
	--name					给容器分配一个名字


# 移除一个或多个容器
$ docker rm [OPTIONS] CONTAINER [CONTAINER...]

OPTIONS选项：
	-f, --force 	强制移除容器(即使容器还在运行)
	-l, --link		移除容器间的网络连接，而非容器本身
	-v, --volumes	移除与容器关联的空间
	--help 			Print usage

# 重命名容器
$ docker rename [OPTIONS] OLD_NAME NEW_NAME

# 显示容器列表
$ docker ps [OPTIONS]

OPTIONS选项：
	-a, --all 		显示所有运行及停止的容器（不加该选项只显示正在运行的容器）


# 停止容器
$ docker stop [OPTIONS] CONTAINER [CONTAINER...]

OPTIONS选项：
	-t, --time=10 	 指定时间后停止容器


# 以dockerfile创建镜像
$ docker build [OPTIONS] PATH | URL | -			# eg: docker build -t <IMAGE_NAME> . （别忘记最后的点号，此时dockerfile文件在当前目录）

OPTIONS选项：
	-t, --tag=[] 	 指定镜像名字及可选的TAG，格式为'IMAGE_NAME:TAG'

# 給镜像打标签
$ docker tag [OPTIONS] IMAGE[:TAG] [REGISTRYHOST/][USERNAME/]NAME[:TAG]


# 查看容器端口映射列表
$ docker port [OPTIONS] CONTAINER [PRIVATE_PORT[/PROTO]]
eg: docker port tomcat		# 查看容器tomcat的端口映射情况

# 退出容器
$ exit 		交互方式启动的容器可以使用ctrl + c 退出容器
 

# 显示镜像的创建历史
$ docker history [OPTIONS] IMAGE

OPTIONS选项：

	-H, --human=true    以可读格式打印大小及日期
	--help              Print usage
	--no-trunc          显示完整的提交记录，不截断输出
	-q, --quiet         仅列出提交记录ID
