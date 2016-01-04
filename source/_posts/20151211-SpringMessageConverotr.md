title: Spring配置MessageConvertor
tags:
  - spring
  - java
categories: java
date: 2015-12-11 00:20:54
---

开发中经常使用Fastjson来进行json数据的封装，不过Spring默认采用的是Jackson，如果需要定义fastjson为默认，你可以进行如下操作：

在你spring启动注解的配置文件中，进行如下配置：

    <mvc:annotation-driven>
        <mvc:message-converters>
            <bean
                class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter">
                <property name="supportedMediaTypes">
                    <list>
                        <value>text/plain;charset=UTF-8</value>
                        <value>text/html;charset=UTF-8</value>
                        <value>application/json</value>
                    </list>
                </property>
                <property name="features">
                    <list>
                        <value>WriteMapNullValue</value>
                        <value>QuoteFieldNames</value>
                    </list>
                </property>
            </bean>
        </mvc:message-converters>
    </mvc:annotation-driven>

<!-- more -->

当然如果配置文件xml顶部声明版本为3.0或者spring版本为3.0都可能出现如下错误

    Element 'mvc:annotation-driven' must have no character or element information item [children], because the type's content type is empty.

所以，尽量升级spring为当前文档的最新版本,将xml的声明修改为3.1及以上！
    
    <beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:context="http://www.springframework.org/schema/context" xmlns:p="http://www.springframework.org/schema/p"
    xmlns:mvc="http://www.springframework.org/schema/mvc" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans  
          http://www.springframework.org/schema/beans/spring-beans-3.2.xsd  
          http://www.springframework.org/schema/context  
          http://www.springframework.org/schema/context/spring-context.xsd  
          http://www.springframework.org/schema/mvc  
          http://www.springframework.org/schema/mvc/spring-mvc-3.2.xsd">


