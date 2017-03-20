---
title: JAVA单例模式
date: 2012-11-09 21:32:11
categories: java
tags: [java,设计模式]
---
Java 的单例模式，即保证在Java应用程序中，一个Java类只有一个实例存在；单例模式可分为饿汉式、懒汉式及登记式（不常用，只做了解即可）。
### 饿汉式
	/** 
	 * @author effine 
	 * @date 2013-9-9  下午11:23:42
	 */  
	package cn.effine.singleton;  
	/* 单例模式：饿汉式 */  
	public class HungrySingleton {  
	    /* 饿汉式单例模式, 声明的同时初始化对象 */  
	    private static HungrySingleton hungry = new HungrySingleton();  
	    /* 构造方法设置成privae，不允许外部实实例化 */  
	    private HungrySingleton() {  
	    }  
	    /* 返回一个单态模式的类的实例 */  
	    public static final HungrySingleton getInstance() {  
	        return hungry;  
	    }  
	}  
单例之饿汉式：对象预先加载，线程安全；在类创建的同时生成单例对象，调用时获得对象实例的方法反应速度快，代码简练。
<!-- more -->
### 懒汉式
	/** 
	 * @author effine 
	 * @date 2013年9月26日  下午1:50:47 
	 */  
	package cn.effine.singleton;  
	/* 单例模式：懒汉式 */  
	public class LazySingleton {  
	    /* 声明的时候不初始化对象 */  
	    public static LazySingleton lazy = null;  
	    /* 将构造器私有化，不允许外部实例化 */  
	    private LazySingleton() {  
	    }  
	    /* 提供对外访问该类对象的方法，多线程下为了资源共享将代码块设置信号量，保证线程安全 */  
	    public static LazySingleton getInstance() { 
	        /* sychronized 用于代码块时需要一个锁对象，针对实例方法可使用this对象；类方法则使用类对应字节码文件对象 */ 
	        synchronized (LazySingleton.class) {
	            if (lazy == null) {
	                lazy = new LazySingleton();  
	            }  
	        }  
	        return lazy;  
	    }  
	} 
单例之懒汉式：对象延迟加载、效率高，非线程安全（为保证线程按照，需对判断代码块加上关键字 synchronized）；在使用时才实例化对象，代码相对于饿汉式复杂，第一次加载类对象的时候反应不快（判断不存在需创建）。

### 登记式
	/** 
	 * @author effine 
	 * @date 2013年9月29日  下午1:43:31 
	 */  
	package cn.effine.singleton;  
	import java.util.HashMap;  
	import java.util.Map;  
	/* 单例模式：登记式 --- 类似Spring里面的方法，将类名注册，下次从里面直接获取 */  
	public class RegisterSingleton {  
	    private static Map<String, RegisterSingleton> map = new HashMap<String, RegisterSingleton>();  
	    static {  
	        RegisterSingleton register = new RegisterSingleton();  
	        map.put(register.getClass().getName(), register);  
	    }  
	    /* 构造方法私有，防止外部实例化 */  
	    private RegisterSingleton() {  
	    }  
	    /* 静态方法返回类的实例 ,参数：map集合的索引名 */  
	    public static RegisterSingleton getInstance(String register) {  
	        if (register == null) {  
	            register = RegisterSingleton.class.getName();  
	        }  
	        if (map.get(register) == null) {  
	            try {  
	                map.put(register, (RegisterSingleton) Class.forName(register)  
	                        .newInstance());  
	            } catch (InstantiationException e) {  
	                e.printStackTrace();  
	            } catch (IllegalAccessException e) {  
	                e.printStackTrace();  
	            } catch (ClassNotFoundException e) {  
	                e.printStackTrace();  
	            }  
	        }  
	        return map.get(register);  
	    }  
	}  