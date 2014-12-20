title: "Hexo Blog Config[2]"
date: 2014-12-20 23:13:18
categories: blog
tags: [blog]
---
发现 `zipperary` 的博客有个酷(niu)炫(bi)的功能：点击设置的链接，页面播放音乐，页面元素随着节奏律动，音乐播放完成，页面恢复正常；转存一下：

<!--more-->

如果你想在博客导航菜单设置效果（当然你还可在其他页面元素部位设置），打开你博客根目录下主题文件夹;我使用的是landscape主题，所以打开文件路径为 `/themes/landscape/layout/_partial/header.ejs`,在博客导航菜单部位添加 `<a>` 标签如下：

	<nav id="main-nav">
        <a id="main-nav-toggle" class="nav-icon"></a>
        <% for (var i in theme.menu){ %>
          <a class="main-nav-link" href="<%- url_for(theme.menu[i]) %>"><%= i %></a>
        <% } %>
		<!-- 添加下面一行代码 -->
		<a class="main-nav-link" href='需要添加下面的js代码'>调皮一下</a>	
     </nav>

注意：添加的超链接`<a>`标签的href属性必须使用单引号 `'` ,因为如下的js代码存在双引号;其次，如下js代码第一行必须和 `href=' ` 自己不存在空格或回车，如 `<a href='javascript:(function() {..其余code..}'>调皮一下</a> `)即可；需要被添加的js代码如下: 

	javascript:(function() {
		function c() {
			var e = document.createElement("link");
			e.setAttribute("type", "text/css");
			e.setAttribute("rel", "stylesheet");
			e.setAttribute("href", f);
			e.setAttribute("class", l);
			document.body.appendChild(e)
		}
	 
		function h() {
			var e = document.getElementsByClassName(l);
			for (var t = 0; t < e.length; t++) {
				document.body.removeChild(e[t])
			}
		}
	 
		function p() {
			var e = document.createElement("div");
			e.setAttribute("class", a);
			document.body.appendChild(e);
			setTimeout(function() {
				document.body.removeChild(e)
			}, 100)
		}
	 
		function d(e) {
			return {
				height : e.offsetHeight,
				width : e.offsetWidth
			}
		}
	 
		function v(i) {
			var s = d(i);
			return s.height > e && s.height < n && s.width > t && s.width < r
		}
	 
		function m(e) {
			var t = e;
			var n = 0;
			while (!!t) {
				n += t.offsetTop;
				t = t.offsetParent
			}
			return n
		}
	 
		function g() {
			var e = document.documentElement;
			if (!!window.innerWidth) {
				return window.innerHeight
			} else if (e && !isNaN(e.clientHeight)) {
				return e.clientHeight
			}
			return 0
		}
	 
		function y() {
			if (window.pageYOffset) {
				return window.pageYOffset
			}
			return Math.max(document.documentElement.scrollTop, document.body.scrollTop)
		}
	 
		function E(e) {
			var t = m(e);
			return t >= w && t <= b + w
		}
	 
		function S() {
			var e = document.createElement("audio");
			e.setAttribute("class", l);
			e.src = i;
			e.loop = false;
			e.addEventListener("canplay", function() {
				setTimeout(function() {
					x(k)
				}, 500);
				setTimeout(function() {
					N();
					p();
					for (var e = 0; e < O.length; e++) {
						T(O[e])
					}
				}, 15500)
			}, true);
			e.addEventListener("ended", function() {
				N();
				h()
			}, true);
			e.innerHTML = " <p>If you are reading this, it is because your browser does not support the audio element. We recommend that you get a new browser.</p> <p>";
			document.body.appendChild(e);
			e.play()
		}
	 
		function x(e) {
			e.className += " " + s + " " + o
		}
	 
		function T(e) {
			e.className += " " + s + " " + u[Math.floor(Math.random() * u.length)]
		}
	 
		function N() {
			var e = document.getElementsByClassName(s);
			var t = new RegExp("\\b" + s + "\\b");
			for (var n = 0; n < e.length; ) {
				e[n].className = e[n].className.replace(t, "")
			}
		}
	 
		var e = 30;
		var t = 30;
		var n = 350;
		var r = 350;
		var i = "//s3.amazonaws.com/moovweb-marketing/playground/harlem-shake.mp3";
		var s = "mw-harlem_shake_me";
		var o = "im_first";
		var u = ["im_drunk", "im_baked", "im_trippin", "im_blown"];
		var a = "mw-strobe_light";
		var f = "//s3.amazonaws.com/moovweb-marketing/playground/harlem-shake-style.css";
		var l = "mw_added_css";
		var b = g();
		var w = y();
		var C = document.getElementsByTagName("*");
		var k = null;
		for (var L = 0; L < C.length; L++) {
			var A = C[L];
			if (v(A)) {
				if (E(A)) {
					k = A;
					break
				}
			}
		}
		if (A === null) {
			console.warn("Could not find a node of the right size. Please try a different page.");
			return
		}
		c();
		S();
		var O = [];
		for (var L = 0; L < C.length; L++) {
			var A = C[L];
			if (v(A)) {
				O.push(A)
			}
		}
	})()

完全按照以上操作，应该能实现！