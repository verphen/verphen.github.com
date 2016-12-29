title: TeamCity配置
tags:
---

本文主要介绍TeamCity关于部署项目的配置，介绍一些常用功能，查看更多参考TeamCity官方文档。首先打开TeamCity界面`<Host|IP>:8111`，参考如下：

- 创建Project(主要配置部署项目所需的外围工具，如Maven、Git等，可视当前需求配置)

	1. 点击右上角Administration -> Create Project -> Manually（手动） 
		![创建项目](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/teamcity/tcc2.png)
	
	2. 填写项目名，自动生成项目ID -> create -> General Settings
		![项目基本配置](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/teamcity/tcc3.png)
		
		Build Configurations： 构建具体项目的部署配置（常用操作）
		
			这里的创建流程和创建Project一样，创建之后左侧的导航栏和父级Project有些差别，粒度更细，针对具体的部署配置。我们可以在左侧导航栏的"Build Steps"制作我们的构建步骤，根据需求制作不同的构建顺序；如Maven编译（Maven的配置在父级）、Command Line（运行shell命令）等。
		
		Build Configuration Templates： 创建构建的模板配置
		
		Subprojects： 在该项目下创建子项目

	3. 点击左侧导航栏`VCS Roots`版本控制系统 -> Create VCS root -> 选择Type of VCS（Git/SVN或其他） -> 查看高级选项`Show advanced options`，配置连接URL、用户名、密码等信息 -> 点击页面底部`Test connection`测试是否可以正常连接
	
	4. 点击左侧导航栏`Parameters` -> Add new parameter -> 配置不同范围级别的常量
		![配置变量](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/teamcity/tcc4.png)
		
		Name: 常量名称
		
		kind: 常量类型；Configuration parameter(配置级别参数)、System property(TeamCity系统级属性，使用默认加上`system.`前缀)、Environment variable(环境变量，使用默认加上`env.`前缀)
		
		Value: 常量值
		
		Spec： 配置常量格式及验证，暂未使用过
		
		注： 定义好不同级别的常量后，可以在项目构建步骤中或添加的shell脚本中使用；用两个百分号括上常量名即可（`%<name>%`）；子级项目继承父级定义的参数，且子级可以重新自定义父级定义的参数值。
		
	5. 点击左侧导航栏`Maven settings`，配置Maven来编译项目 -> Upload settings file -> 弹出框添加名称，选择待上传的mave/conf/setting.xml文件即可
		![配置变量](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/teamcity/tcc5.png)

	6. 点击左侧导航栏`Clean-up Rules`，配置清理TeamCity残留文件 -> 点击待配置项目尾部的`Edit`
		![配置项目清理规则](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/teamcity/tcc6.png)
		
		根据需求可以选择不同的策略，选择`Custom policy`自定义策略：清除超过多少天前的构建；清理多少个成功构建之前的构建。当然你可配置每天定时清理：右上角Administration -> 右侧导航栏Clean-up Settings -> 配置

- 配置TeamCity插件

在官方提供的插件库[https://plugins.jetbrains.com/?teamcity](https://plugins.jetbrains.com/?teamcity)搜索下载你需要安装的插件，然后上传你下载的插件至安装的TeamCity即可: 点击右上角Administration -> 点击左侧导航栏底部的`Plugins List` -> `Upload plugin zip` -> 填写名称，选择插件文件上传即可
![安装插件](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/teamcity/tcc7.png)
