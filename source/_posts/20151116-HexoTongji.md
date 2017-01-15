title: Hexo 博客配置访问统计
date: 2015-11-16 17:33:44
tags: [hexo]
categories: tools
---
常用的网站统计无非是google analytics(博客默认，国内访问不流畅)、[百度统计](http://tongji.baidu.com/)和[CNZZ](http://cnzz.com/)，怎么配置？先去对应的网站配置获取js代码，然后加入你网站的footer即可（有的加入head标签内；不过推荐放在footer，不影响页面加载）; Hexo博客添加统计代码都是添加在主题theme代码中（本站当前采用的是landscape主题），以当前主题来讲解添加百度统计，其他主题配置大同小异。

	# 以下内容来源网络
	1.编辑文件 themes/landscape/_config.yml,使用"#"注释原来的google analytics，添加百度统计配置行
	
		baidu_tongji: true      # 百度统计
	
	2.新建 themes/landscape/layout/_partial/baidu_tongji.ejs 内容如下
	
		<% if (theme.baidu_tongji) { %>
		# 百度统计代码可能已经包含标签<script>,视情况而定
		<script type="text/javascript">
			# 申请的百度统计代码
		</script>
		<% } %>
	
	3.编辑themes/landscape/layout/_partial/footer.ejs 在 <div class="outer"></div> 标签内添加
		
		<%- partial("baidu_tongji") %>
	
	4.重新生产部署站点即可。

当然，对于 CNZZ 统计的添加类似如上操作即可。