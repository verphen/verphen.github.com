title: "Robots"
date: 2015-05-21 19:37:54
categories: web 
tags:
  - web
  - 运维
---

整个网站都不想暴露在搜索引擎下，在网站根目录添加 robots.txt 文件

# 禁止被搜索引擎收录和网络蜘蛛爬行
User-agent: *
Disallow: /




单个页面不想被搜索引擎收录和网络蜘蛛爬行，在页面顶部加上 META NAME="ROBOTS" 标签。