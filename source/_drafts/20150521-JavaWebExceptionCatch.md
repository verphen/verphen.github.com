title: Java Web Exception Catch
date: 2015-05-21 16:37:54
categories: 
tags:
  - java
  - exception
---


<!-- 全局异常配置 -->
    <bean id="exceptionResolver"
        class="org.springframework.web.servlet.handler.SimpleMappingExceptionResolver">
        <!-- 定义默认的异常处理页面 -->
        <property name="defaultErrorView" value="common/500"></property>

        <!-- 定义需要特殊处理的异常，用类名或完全路径名作为key，异常页面名作为值 -->
        <property name="exceptionMappings">
            <props>
                <prop key="java.lang.Exception">common/500</prop>
                <prop key="java.lang.Throwable">common/500</prop>
            </props>
        </property>
        <property name="statusCodes">
            <props>
                <prop key="common/404">404</prop>
                <prop key="common/500">500</prop>
            </props>
        </property>
        <!-- 设置日志输出级别，不定义则默认不输出警告等错误日志信息 -->
        <property name="warnLogCategory" value="WARN"></property>
        <!-- 默认HTTP状态码 -->
        <property name="defaultStatusCode" value="500"></property>
    </bean>