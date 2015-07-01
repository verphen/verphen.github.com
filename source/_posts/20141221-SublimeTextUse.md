title: 使用sublime text 3
date: 2014-12-21 22:05:51
categories: tools
tags: [tools,sublime]
---
官网 [http://www.sublimetext.com/](http://www.sublimetext.com/) 下载安装sublime

插件安装存在两种方式：

- 下载安装

    下载待安装插件文件到Packages目录（菜单栏 -> preferences -> browse packages）

- 使用package control组件安装

    使用package control安装插件，必须先安装package control组件;如果已安装跳过即可，未安装按如下方式进行安装

    。ctrl + ` : 调出console面板，弹出框输入一下code回车
    
        import urllib.request,os; pf = 'Package Control.sublime-package';
        ipp = sublime.installed_packages_path(); urllib.request.install_opener(
        urllib.request.build_opener( urllib.request.ProxyHandler()) ); 
        open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen(
        'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
	
    <!-- more -->
    
	如果你sublime text 版本为2，输入的code则为：

	    import urllib2,os; pf='Package Control.sublime-package'; 
        ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not
        os.path.exists(ipp) else None; urllib2.install_opener( 
        urllib2.build_opener( urllib2.ProxyHandler( ))); 
        open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen(
        'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); 
        print( 'Please restart Sublime Text to finish installation')

    。重启sublime,Perferences菜单能看到package control这一项，则说明安装成功

    。ctrl + shift +p 快速打开package control，或者preferences -> package control打开；输入 `install package ` 回车，等待repositories加载完成弹出输入框，输入你要安装的插件名 -> 搜索 -> 选择 -> 回车  



