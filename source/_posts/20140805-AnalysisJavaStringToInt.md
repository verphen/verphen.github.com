title: Java字符串转String换成整形int的分析
date: 2014-08-06 06:54:25
categories: java
tags: [java,efficiency]
---
针对Java的String类型转换成int的技巧和思考：

- 转换技巧

		 方案一： 
		> Integer.parseInt(String s);
		> Integer.parseInt(String s, int radix);
	
	查阅jdk源码发现，发现 `Integer.parseInt(String s)` 方法调用int的包装类Integer的parseInt(s,10)方法，即就是 `Integer.parseInt(String s,int radix)`,解析字符串s使用的基数radix(进制数)，转换成有符号的整数
	
		 方案二：
		> Integer.valuseOf(String s);
		> Integer.parseInt(String s, int radix)
		
	方法valueOf(String s)的底层实现： 调用 `Integer.valueOf(parseInt(s,10))`; 类似，方法valueOf(String s,int radix)底层调用 `Integer.valueOf(parseInt(s,radix))`

- 分析比较

	parseInt方法只是将String转换成int基本数据类型，而valueOf则是将String转换成Integer包装对象；
	
	若将以上两种转换方式放入具体的场景：

	1. 简单转换String为int： 建议调用 ` Integer.parseInt(s,10) `(ps: s为字符数String类型，10为指定的转换基数radix),这样理论上是可以提高程序的执行效率。
	
	2. 如需转换String为对应Integer，建议选择 ` Integer.valueOf(String s, int radix) `