
spring-boot启动方式：

	> idea run with
		运行包含 @SpringBootApplication 注解的类的main方法即可
	> mvn spring-boot:run
	> java -jar ***.jar


注解 @SpringBootApplication 相当于一下三个注解：
	@Configuration：表示将该类作用springboot配置文件类。
	@EnableAutoConfiguration:表示程序启动时，自动加载springboot默认的配置。
	@ComponentScan:表示程序启动是，默认自动扫描当前包及子包下所有类（所以默认添加注解 @SpringBootApplication 的类应默认放在groupId包下，便于扫描当前包及其子包的类）。


如果必须把 springBoot 的启动类放在其他目录(非顶级目录)，可以使如下注解：
	@SpringBootApplication
	// xx.xx.xx 是待扫描的包路径
	@ComponentScan(value = "xx.xx.xx")




springBoot的文章：10.1    https://qbgbook.gitbooks.io/spring-boot-reference-guide-zh/content/