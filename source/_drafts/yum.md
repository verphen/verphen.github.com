[root@effine unixODBC-2.2.1]# yum --help
已加载插件：fastestmirror
Usage: yum [options] COMMAND

List of Commands:

check          Check for problems in the rpmdb
check-update   检查是否有软件包更新
clean          删除缓存的数据
deplist        列出软件包的依赖关系
distribution-synchronization Synchronize installed packages to the latest available versions
downgrade      downgrade a package
erase          从系统中移除一个或多个软件包
groupinfo      显示组的详细信息
groupinstall   向系统中安装一组软件包
grouplist      列出可安装的组
groupremove    从系统中移除一组软件包
help           显示用法信息
history        Display, or use, the transaction history
info           显示关于软件包或组的详细信息
install        向系统中安装一个或多个软件包
list           列出一个或一组软件包
load-transaction load a saved transaction from filename
makecache      创建元数据缓存
provides       查找提供指定内容的软件包
reinstall      覆盖安装一个包
repolist       显示已配置的仓库
resolvedep     判断哪个包提供了指定的依赖
search         在软件包详细信息中搜索指定字符串
shell          运行交互式的 yum 外壳
update         更新系统中的一个或多个软件包
upgrade        更新软件包同时考虑软件包取代关系
version        Display a version for the machine and/or available repos.


Options:
  -h, --help            show this help message and exit
  -t, --tolerant        容忍错误
  -C, --cacheonly       run entirely from system cache, don't update cache
  -c [config file], --config=[config file]
                        配置文件路径
  -R [minutes], --randomwait=[minutes]
                        命令最长等待时间
  -d [debug level], --debuglevel=[debug level]
                        调试输出级别
  --showduplicates      在 list/search 命令下，显示仓库里重复的条目。
  -e [error level], --errorlevel=[error level]
                        错误输出级别
  --rpmverbosity=[debug level name]
                        debugging output level for rpm
  -q, --quiet           安静的操作
  -v, --verbose         verbose operation
  -y, --assumeyes       回答所有的问题为是
  --version             显示 Yum 版本信息并退出
  --installroot=[path]  设置目标根目录
  --enablerepo=[repo]   启用一个或多个仓库(支持通配符)
  --disablerepo=[repo]  禁用一个或多个仓库(支持通配符)
  -x [package], --exclude=[package]
                        用全名或通配符排除软件包
  --disableexcludes=[repo]
                        禁止从主配置，从仓库或者从任何位置排除
  --obsoletes           升级时考虑软件包取代关系
  --noplugins           禁用 Yum 插件
  --nogpgcheck          禁用 gpg 签名检测
  --disableplugin=[plugin]
                        禁用指定名称的插件
  --enableplugin=[plugin]
                        enable plugins by name
  --skip-broken         跳过有依赖问题的软件包
  --color=COLOR         配置是否使用颜色
  --releasever=RELEASEVER
                        set value of $releasever in yum config and repo files
  --setopt=SETOPTS      set arbitrary config and repo options