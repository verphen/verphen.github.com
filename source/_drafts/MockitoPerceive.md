title: Mockito 初识
categories: tools
tags: [mock,mockito]
---



@Mock 与 @InjectMocks 区别：
> Mock 注解的接口会被 Mock 阻断，程序执行流无法通过接口调用方法（一般回报NPE异常）
> InjectMocks 注解接口，相当于将接口的实现注入当前类，可通过该接口调用其方法

 
 验证方法是否被调用，以及方法调用的次数，方法调用的顺序
 given方法

 junit 的 @Before

