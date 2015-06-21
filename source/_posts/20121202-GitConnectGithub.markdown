---
title: Git Connect GitHub
date: 2012-12-02 13:40:43
categories: tools
tags: [git,github]
---
怎么使用GitHub作为代码的远程托管服务器？

1. 在GitHub创建账户，然后创建一个 Repository（仓库、储存室），创建过程有提示，这里就不再赘述。

2. 本机创建SSH key：`ssh -keygen -C "username@email.com" -t rsa`(ps:username@email.com为你在GitHub上使用的email)；运行该命令之后在你电脑的`C:\Users\本机用户名`路径下产生一个.ssh文件夹，里面对应SSH Keys，其中id_rsa.pub是GitHub需要的SSH公钥文件。然后在GitHub网站右上角选择Account Settings，然后选择SSH Keys，点击Add SSH Key，将id_rsa.pub文件里的内容copy至其中的key里（Title随意）；当然如果之前你使用过SSH Keys命令需要删除.ssh文件夹然后重新开始。

3. 验证SSH keys：`ssh -T git@github.com`,仔细看描述信息

5. 设置全局变量(暂且这么称呼)username：`git config  --global user.name "usernme"`(username：GitHub的用户名）, Email：`git config  --global user.email emailName`（emailName：GitHub的注册邮箱） 

6. 克隆GitHub上的仓库`git clone ` 

4. 在本地创建一个工程（文件夹），在该目录下随意创建一个文件（如readme.txt，在文件中写点内容，最好是英文；如果是中文需要以uft-8编码格式进行保存，因为GitHub上默认使用utf-8编码格式）；git bash进入工程目录（如需要进入D盘`cd ./d:`， 然后cd到工程目录下），输入命令`git init`初始化工程。

5.  使用`git add filename`(filename包括后缀) 将文件添加到git库(即将文件交给git管理)；命令`git add .`是添加所有文件和文件夹。

6.  使用`git commit -m "commit message"`进行提交git本地库

12. 使用远程连接：git remote add origin git@github.com:username/Hello.git （username：GitHub上的用户名，Hello：我在GitHub上创建的仓库repository名）

13.  输入命令“git push origin master”将源码推送到GitHub

14.  在GitHub上仓库页面刷新即可看到你在本地创建并提交的文件

推荐各位使用GitHub的客户端工具，界面做得确实不错。  

- windows: [https://windows.github.com/](https://windows.github.com/) 
- mac: [https://mac.github.com/](https://mac.github.com/)