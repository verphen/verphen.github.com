
spring-boot启动方式：

	> idea run main method
		运行包含 @SpringBootApplication 注解的类的main方法即可
	> mvn spring-boot:run
	> java -jar ***.jar
	  java -jar ***.jar --debug 	启用debug


注解 @SpringBootApplication 相当于一下三个注解：
	@Configuration：表示将该类作用springboot配置文件类。
	@EnableAutoConfiguration:表示程序启动时，自动加载springboot默认的配置。
	@ComponentScan:表示程序启动是，默认自动扫描当前包及子包下所有类（所以默认添加注解 @SpringBootApplication 的类应默认放在groupId包下，便于扫描当前包及其子包的类）。


如果必须把 springBoot 的启动类放在其他目录(非顶级目录)，可以使如下注解：
	@SpringBootApplication
	// xx.xx.xx 是待扫描的包路径
	@ComponentScan(value = "xx.xx.xx")

	@SpringBootApplication注解也提供了用于自定义@EnableAutoConfiguration和@ComponentScan属性的别名（aliases） ？

	Spring Boot支持以远程调试模式运行一个打包的应用，下面的命令可以为应用关联一个调试器：
	$ java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n \
       -jar target/myproject-0.0.1-SNAPSHOT.jar


Thymeleaf模板设置

application.properties文件的配置：

	spring.thymeleaf.cache  缓存设置
	spring.devtools.restart.exclude
	spring.devtools.restart.additional-exclude

	spring.devtools.restart.additional-paths 	添加其他监控路径(修改后自动重启或者重新加载)
	spring.devtools.restart.enabled 	禁用重启(依旧会初始化重启类加载器)

	// 彻底禁用文件变化应用重启
	public static void main(String[] args) {
	    System.setProperty("spring.devtools.restart.enabled", "false");
    	SpringApplication.run(MyApp.class, args);
	}

	spring.devtools.restart.trigger-file 	 配置触发器文件(该文件变化才会触发重启)
	spring.devtools.livereload.enabled 		配置livereload开启禁用状态(每次只能运行一个LiveReload服务器，如果你在IDE中启动多个应用，只有第一个能够获得动态加载功能)

	spring.devtools.remote.debug.local-port 	远程调试自定义端口

可以设置全局的application.properties配置，在用户目录创建文件".spring-boot-devtools.properties"即可




spring-boot-actuator
development-time配置
JRebel
SpringApplication.setRegisterShutdownHook(false)
自定义banner
 
springBoot的文章：

	https://qbgbook.gitbooks.io/spring-boot-reference-guide-zh/content/