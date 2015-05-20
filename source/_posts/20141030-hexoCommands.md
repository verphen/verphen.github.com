title: Hexo Commands
date: 2014-10-30 08:14:27
categories: tools
tags: [tools,hexo]
---
<h3>博客搭建工具hexo基本命令：</h3>

- hexo help(hexo h): Get help on a command; 获得命令帮助，你也可以使用 `hexo help [command]`命令获得详细帮助(如hexo help clean),当然你可以访问 <a href="http://hexo.io/docs">http://hexo.io/docs/</a>  获得详细信息。（很多其他工具同样会提供这样的命令，如git help等，可能形式不同而已: hexo h、 hexo -help、 hexo --help、 hexo -?、 hexo --?]等）;

<!--more-->

<img src="/imgs/hexo_help.png" alt="hexo help" />

- hexo init:　Create a new Hexo folder；初始化一个Hexo文件夹

- hexo new "article name"(hexo n "article name"): Create a new post；新建post文章

- hexo generate(hexo g): 生成静态文件

- hexo draft: Publish a draft; 发布草稿

- hexo server(hexo s): 启动本地服务进行文章预览（默认预览地址 localhost:4000）

- hexo deploy(hexo d): Deploy your website; 部署,如部署至github

- hexo d -g; 组合命令：生成本地静态文件并部署

- hexo clean: Remove generated files and the cache;删除已生成的静态文件和缓存

- hexo config: List the current configuration；查看当前所有的配置信息列表

- hexo list:　List the information of the site；　你站点的信息列表

- hexo migrate: Migrate your site from other system to Hexo;将你的站点从其他系统迁移至hexo

- hexo render: Render the files with Markdown or other engines; 使用Markdown或其他引擎渲染文件

- hexo version: Display version information; 显示hexo和相关环境的版本信息

Global Options 全局选项:

- hexo - -config: Specify config file instead of using _config.yml; 自定义配置文件替换 _config.yml

- hexo - -debug: Display all verbose messages in the terminal; 调试模式，终端显示所有详细信息

- hexo - -safe: Disable all plugins and scripts; 禁用所有的插件和脚本

- hexo - -silent: Hide output on console; 在控制台隐藏输出