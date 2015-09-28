title: Eclipse 快捷键
tags:
  - eclipse
  - shortcut
categories: tools
date: 2015-07-07 09:27:14
---
对于java开发，eclipse是必不可少的IDE，现整理其使用快捷键如下：

	ctrl + / 	# 注释与取消注释当前行
	ctrl + shift + c 	# 注释与取消注释当前行

    ctrl + shift + /    # 注释选中的行（多行注释/* content */ ）
    ctrl + shift + \    # 取消选中的注释行（多行注释）

	alt + shift + j 	# 文档注释；给变量、方法、类添加描述(方法会列出参数和返回值等)
	
	ctrl + o 	# 弹框搜索当前类的方法和全局变量
	ctrl + shift + o 	# 自动导入必须包;
						  鼠标焦点在当前java文件内，则只针对当前文件；如果焦点在整个工程，则针对项目所有的文件
	ctrl + shift + r 	# 查找并打开资源文件
	ctrl + shift + g 	# 定位或选中方法名或变量名再使用快捷键，搜索列出所有调用此该方法或使用变量的地方
	ctrl + shift + h 	# 搜索包含指定内容的文件或其他,选择 "file search" 则搜索文件;
 						  点击左下角的 "customize...",可以控制显示的标签tab和上次打开的page
    ctrl + shift + x    # 将选中的字母变为大写
    ctrl + shift + y    # 将选中的字母变为小写
    
<!-- more -->

    ctrl + .	# 定位下一处错误或者警告
    ctrl + 1 	# 列出 eclipse 提供的解决方案
    ctrl + 3 	# 打开Quick Access搜索（搜索eclipse菜单、标签等）

    ctrl + g 	# 搜索定位方法名或变量的所有方法或变量
    ctrl + t 	# 查看定位方法的继承树
    ctrl + 鼠标右键点击(变量或方法) 	# 进入其定义或实现
    ctrl + l 	# 跳转到指定行号的行
    
    alt + / 	# 显示提示信息
    alt + 左右方向键 	# 后退/前进"ctrl+鼠标右键点击"的跳转流程或操作位置
    alt + 上下方向键 	# 将当前行与上/下行交换位置
    ctrl + alt + 上下方向键 	# 复制当前行到上/下一行

    shift + enter 	# 当前行下一行插入空行
    ctrl + shift + enter 	# 当前行上一行插入空行

    alt + shift + r 	# 修改文件名、方法名、变量名,并更新其引用
    alt + shift + a 	# eclipse列模式, 划定区域输入内容回车即可
    alt + shift + o(字母)     # 切换标记发生(toggle mark occurrences);
                               把选中的方法/变量在本类中全部出现的地方高亮显示

调试模式的快捷方式：
	
    ctrl + shift + i 	# 显示复制的代码执行的值

skill:

    - 输入"syso"然后按 alt + / , 则输出 " System.out.println(); "
    - 输入"syse"然后按 alt + / , 则输出 " System.err.println(); "