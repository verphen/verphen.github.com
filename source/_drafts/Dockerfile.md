title: Dockerfile
tags:
---



FROM     基础镜像 (可以多个，每个镜像一次)
MAINTAINER      定义作者
ADD <source file>  <cotainer dir>    移动dockerfile同级目录文件至容器内目录
RUN     镜像中运行命令
EXPOST      设置镜像运行时暴露在外的端口