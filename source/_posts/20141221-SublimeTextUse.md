title: Use Sublime Text 3
date: 2014-12-21 22:05:51
categories: tools
tags: [tools,sublime]
---
<h3>Install Sublime</h3>

官网 <a href="http://www.sublimetext.com/" >http://www.sublimetext.com/</a>下载安装即可

<h3>Install plugin</h3>

- 下载安装

	下载安装包解压缩到Packages目录（菜单栏->preferences->packages）

- 使用package console组件安装

	使用 package console 组件安装sublime text插件，必须先安装package console组件:

	<!-- more -->	

	- contrl + ` : 调出console面板，明了了框输入一下code，Enter

		import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
	
		如果你sublime text 版本为2，输入的code则为：

		import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')

	- 重启sublime,Perferences->package settings中看到package control这一项，则说明安装成功

	- 使用package console 安装插件（待续----）

	
	