title: Vi Commands
date: 2015-01-10 22:36:25
categories: linux
tags: [linux,tools]
---
vi编辑器在Linux下使用频率不言而喻，简单收集整理：

- vi filename -- 使用vi编辑器对文件filename进行编辑（Enter进入命令模式）

- 命令模式下的命令（编辑模式切换到命令模式，按ESC键即可）

	- :w -- 保存文件但不退出vi编辑器
	- :w filename -- 将修改的文件另存为filename,不退出vi
	- :w! -- 强制保存，不退出vi
	- :q -- 退出vi
	- :q! -- 强制退出vi
	- :wq -- 保存并退出vi 
	- :wq! -- 强制保存并退出vi
	- :e! -- 放弃所有修改，从上次保存文件处开始再次编辑

	- :lineNo -- 调转到指定行号（lineNo）行首
	- /keyword -- 搜索关键字(按'n'定位下一处匹配)
	 
- 编辑模式 （命令模式切换到编辑模式，按'i'即可，vi编辑器下发会出现"insert"样式）

