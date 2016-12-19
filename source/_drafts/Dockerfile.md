title: Dockerfile
tags:
---




FROM     基础镜像 (可以多个，每个镜像一次)
MAINTAINER      定义作者
ADD <source file>  <cotainer dir>    移动dockerfile同级目录文件至容器内目录
RUN     镜像中运行命令
EXPOST      设置镜像运行时暴露在外的端口

RUN 执行命令默认在根目录('/'), 同一条RUN命令执行的目录相同，前面的RUN命令进入的目录不能带到下一条RUN命令(即就是下一条RUN命令默认目录在根目录)


#certification dir
RUN cd / & mkdir /install 