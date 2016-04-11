
upsource 与 pull reqquest的分析
 

### 简介

* Upsource

        JetBrains公司（IntelliJ IDEA所属公司）推出，专门为软件开发团队所设计的源代码协作工具,主要作code review使用;

* pull request

		 依托Git Server图形界面管理工具gitlab来实现，其主要扮演把你在当前分支（功能分支）的修改合并到稳定分支（dev或master）前代码对比的角色，审核人通过对比两个分支代码变化来进行代码审核，以确定是否需要合并当前功能分支修改到稳定分支（代码合并人一般是审核人）
        
### 操作流程
	
依托图形界面操作演示

* [upsource](http://10.201.201.97:8081/) 
		.  username:   comall
		.  passwd:   comall
* [pull request](http://gitlab.product.co-mall:10080/)
	
### 分析

* upsource
 
	针对对象： 某一分支的所有提交
	用户提交的 
	代码对比对象:  选择的两个分支
	
	<br>
* pull request
 
	 针对对象： 一段时间内(用户新建pull request时间内)代码修改的提交
	 代码对比对象:  选择的两个分支

综合分析：
* 两种工具都是以对代码进行对比实现代码审查
* 都是以用户选择的两个分支代码来进行对比；
* 都可以针对某一次提交进行评论、对文件某一行进Upsource行描述注释；
<br>
* upsource是针对分支内所有的提交，而pull request则根据用户新建pull request时间内的提交（更加片段化、功能化）；
* pull request需要涉及多个分支来隔离团队成员的提交而实现互相审核；而upsource是使用过滤条件来隔离团队成员的提交；
 
### issure

Q：  什么时候创建pull request合适？
A ：  http://www.infoq.com/cn/news/2015/02/pull-reques-ten-suggestion
  

