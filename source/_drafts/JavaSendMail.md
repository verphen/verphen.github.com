title: JavaSendMail
date: 2015-04-16 22:12:45
categories: java
tags:
  - java
  - mail
---
程序代码显示：

	public static void sendYunluEmail(){
		String subject = "面试邀请"; // 主题
		HtmlEmail email = new HtmlEmail();
		//email.setHostName("124.192.148.36"); // 设置发信的smtp服务器
		email.setHostName("mail.yunlu.me");
		email.setSubject(subject); // 设置邮件主题
		email.setAuthentication("noreplay@mail.yunlu.me","*****");// SMTP服务器认证,设置帐号、密码
		email.setCharset("utf-8"); // 设置邮件字符集
		try {
			email.addTo("verphen@163.com", "effine"); // 设置收件人帐号和收件人
			email.setFrom("noreplay@mail.yunlu.me","wu wang"); // 设置发信的邮件帐号和发信人
			email.setHtmlMsg("邮件内容 email content"); // 设置邮件正文，此方法这里的样式可以显示出来
			email.send();
			System.err.println("邮件发送成功");
			
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

网易邮箱SMTP： smtp.163.com
腾讯邮箱SMTP： smtp.qq.com
或者自己配置的邮件服务器