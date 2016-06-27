title: DockerMachineCommands
tags:
---

$ docker-machine ssh default	# 连接docker默认虚拟机(用户名docker / 密码tcuser)
     

属性docker-machine命令
     docker-machine ls      # 列出所有docker machine
     docker-machine create - - driver virtualbox default      # 创建新的docker虚拟机;
     docker-machine env default      # 获取虚拟机default的环境变量
     eval “$(docker-machine env default)”     # 连接到default虚拟机
     docker-machine rm <machine-name>     # 删除某台虚拟机
     docker-machine start <machine-name>     # 启动虚拟机
      $ docker-machine restart default      #  重启docker虚拟机default

 