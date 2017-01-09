title: Dockerfile 基本语法
tags: [docker,tools]
catagories: docker
date: 2017-01-09 23:04:51
---
Dockerfile指令不区分大小写，默认约定大写；该文件必须以FROM命令开始，其意义为指定基础镜像；FROM命令可多次使用，表示会创建多个镜像
    
    FROM <IMAGE>  # 指定基础镜像
    MAINTAINER <author>  <email>   # 指定创建Dockerfile作者及邮箱
    RUN  <COMMAND>      # 新镜像上执行命令（每一条RUN执行的命令默认目录都是根目录'/'）
       
    # 添加宿主机文件至容器内，若是压缩包会自动解压
    ADD  <localhost dir | URL > <container dir> 

    # 只是添加宿主机文件至容器，不处理压缩包文件，ADD命令简化版
    COPY  <localhost dir>  <container dir>   

    WORKDIR <path>      # 指定RUN、CMD、ENTRYPOINT命令的工作目录
<!-- more -->
    USER <uid>      # 设置镜像运行时的UID
    ENV <key> <value>   # 设置镜像环境变量

    VOLUME <container path>  # 设置容器待挂载目录，配合docker启动命令使用
    $ docker run -v <localhost dir>   # 表示容器目录path挂载到宿主机目录(localhost dir)
    $ docker run -v <localhost dir>:<container path>  # 该命令执行效果同上 

    EXPOSE <port>   # 指定容器运行时监听的端口

    # 容器默认执行命令，Dockerfile只允许使用一次CMD；若多个只执行最后一个
    ENTRYPOINT ["executable", "param1", "param2", ...]
    ENTRYPOINT ["param1","param2", ...]

    # 容器默认执行命令，Dockerfile只允许使用一次CMD；若多个只执行最后一个
    CMD ["executable", "param1", "param2", ...]
    CMD ["param1","param2", ...]
    CMD command param1 param2 ...

注：ENTRYPOINT执行命令不会被ocker容器启动时指定命令(容器名后面接的内容)覆盖，而是作为参数传递进去(即连接到ENTRYPOINT执行命令后面)；而CMD执行命令会被Docker容器启动的命令覆盖。如果同时存在ENTRYPOINT和CMD，那么ENTRYPOINT是默认执行命令，且CMD作为ENTRYPOINT的参数；如果没有ENTRYPOINT，则CMD就是默认执行指令。
 

 
