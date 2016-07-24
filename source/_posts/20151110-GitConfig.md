title: Git Config
tags:
  - config
  - git
categories: git
date: 2015-11-10 18:17:52
---

Git配置存在适用范围：

-  项目范围： `git config`    # 保存在项目根目录.git/config文件
-  系统用户范围： `git config - -global`      # 保存在用户根目录.gitconfig文件

便于使用，我们通常配置系统用户范围；一些具体配置如下

	# 列出所有配置,grep可过滤具体Command命令
	$ git config --list	[| grep command]
	$ git config -l [| grep command]

	$ git config --global user.name "username"     # 设置全局用户名(提交历史可见)
    $ git config --global user.email "email"     # 设置全局邮箱(提交历史可见)
    $ git config --global color.ui <true|false>   # Git会显示适当地颜色[打开|关闭]
    $ git config --global core.editor <emacs>       # 设置文本编辑器emacs
    $ git config --global merge.tool <vimdiff>      # 设置差异分析工具vimdiff
     
    # 设置命令别名；命令别名列举(可自定义其他别名)
	$ git config --global alias.<aliasname> <command> 	# 使用别名aliasname代替command
	$ git config --global --unset alias.<aliasname>   # 取消别名aliasname设置
		> status [st]
		> commit [ci]
		> checkout [co]
		> branch [br]
		> diff [df]
        > cherry-pick [cp]
	# 配置完别名之后，将在对应配置文件产生记录(可直接在该文件配置)
		[alias]  
	      st = status  
	      ci = commit  
	      br = branch  
	      co = checkout  
	      df = diff 
          cp = cherry-pick
	   
	# 处理不同平台换行操作符(如警告: warning: LF will be replaced by CRLF in ...)
    $ git config  --global  core.autocrlf <false|true> 

	$ git config  --global --unset-all core.ignorecase    # 取消所有关于是否忽略Git大小写的设置
	$ git config  --global --system core.ignorecase <false|true>   # 设置Git是否忽略大小写