title: 搭建Docker仓库
tags:
---

docker搭建私有仓库(使用直接拉取官方镜像来搭建)：
     $ docker pull registry     # 拉取官方镜像
     $ mkdir  /registry     # 创建本地目录来存放上传镜像
     $ docker run -p 5000:5000 -v /registry:/var/lib/registry -d --name local_registry registry      # 启动私有仓库镜像
     $ curl -i 192.168.99.100:5000  # 验证镜像是否正常（ip为docker虚拟机default的ip）

     // 配置default虚拟机，指定docker私有仓库
     $ sudo  vi /var/lib/boot2docker/profile
          EXTRA_ARGS='
--label provider=virtualbox
# 下面是你搭建私有仓库的地址
--insecure-registry 192.168.99.100:5000
'

     $ docker tag local_images 192.168.99.100:5000/local_images          # 给本地镜像制作tag
     $ docker push 192.168.99.100:5000/local_image    # push你创建好tag的镜像到私有仓库