title: BrewCommands
tags:
---

brew install <softName>     # 安装指定软件

brew services list      # 查看运行在当前用户下的服务状态
brew services <servicesName> <start|stop|restart>   # 服务的启动/停止/重启

brew search <name>  # 搜索软件名
brew info <name>    # 查看软件信息(版本、依赖、安装事项)
brew update         # 更新Homebrew自身
brew outdated       # 检测包是否为最新
brew upgrade [name] # 升级软件
brew cleanup        # 清理软件安装历史版本及安装包缓存
brew link           # 


Homebrew cask 的使用