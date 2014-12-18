---
title: JAVA单例模式
date: 2012-11-09 21:32：11
categories: java
tags: [java,设计模式]
---
作用：保证在Java应用程序中，一个Java类只有一个实例存在；所以一般单态类会提供一个返回该类实例的方法。提供一个对对象的全局访问指针。

优点：节省内存，限制类的个数，有利于Java的垃圾回收机制（Garbage Collection ）；

缺点及注意点：

* 多线程情况下，懒加载模式可能导致线程不安全因素，例如：同时有两个线程同时调用getInstance方法获取实例时，可能两个线程同时进入if语句判断块，此时类尚未被实例化，那么将同时得到两个不同的实例（此注意点比较容易避免，获取实例时使用同步sync就可以很好的解决）。
* 当单例类被多个classloader加载的情况下，可能获得多个单例类的实例（此种情况可能比较难避免，这需要使所有的类使用相同的类加载器加载）。
* 当单例类实现了序列化接口（Serializer）时，我们如果将对象序列化，并返回序列化得到实例时，这个实例将是一个新的实例，而不是序列化之前的实例（在这种情况下，需要在此类中添加readResolve方法，将返回对象设置为当前实例，否则会获得一个不同于序列化之前的类）。
单例模式具体分为饿汉式、懒汉式及登记式（这个很少介绍）：

1、饿汉式  HungrySingleton.java
	/** 
	 * @author Verphen 
	 * @date 2013-9-9  下午11:23:42 
	 */  
	  
	package org.verphen.singleton;  
	  
	/*单例模式：饿汉式*/  
	public class HungrySingleton {  
	  
	    /* 饿汉式单例模式,声明的同时初始化对象 */  
	    private static HungrySingleton hungry = new HungrySingleton();  
	  
	    /* 构造方法设置成privae，即实现了单态 */  
	    private HungrySingleton() {  
	    }  
	  
	    /* 返回一个单态模式的类的实例 */  
	    public static final HungrySingleton getInstance() {  
	        return hungry;  
	    }  
	}  
2、懒汉式  LazySingleton.java
	/** 
	 * @author VerpHen 
	 * @date 2013年9月26日  下午1:50:47 
	 */  
	  
	package org.verphen.singleton;  
	  
	/*单例模式：懒汉式*/  
	public class LazySingleton {  
	  
	    /* 声明的时候不初始化对象 */  
	    public static LazySingleton lazy = null;  
	  
	    /* 将构造器私有化，不对外提供构造器 */  
	    private LazySingleton() {  
	    }  
	  
	    /* 提供对外访问该类对象的方法，多线程下为了资源共享将代码块设置信号量，保证线程安全 */  
	    public static LazySingleton getInstance() {  
	  		synchronized (LazySingleton.class) {
	        	if (lazy == null) {  
	            	/* sychronized用于代码块时需要一个锁对象，针对实例方法使用this对象； */  
	           		/* 当针对类方法时可以使用该类对应的字节码文件对象，this这个时候不存在 */  
	                lazy = new LazySingleton();  
	            }  
	        }  
	        return lazy;  
	    }  
	}  
引用文章针对上面代码（lazy=new LazySingleton();）有加上一次if判断（if(lazy==null) ），给出的理由是“采用双重判断，提高了多线程下操作的效率”；我认为没能提高效率，所以去掉多余的if判断；（ps：如有见解，欢迎指正探讨）

3、登记式  RegisterSingleton.java
	/** 
	 * @author VerpHen 
	 * @date 2013年9月29日  下午1:43:31 
	 */  
	  
	package org.verphen.singleton;  
	  
	import java.util.HashMap;  
	import java.util.Map;  
	  
	/*单例模式：登记式 --- 类似Spring里面的方法，将类名注册，下次从里面直接获取*/  
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
分析饿汉式和懒汉式：

饿汉式是以预先加载方式加载对象；不管是单线程还是多线程都是线程安全的；懒汉式则以延迟加载方式加载对象；单线程没有任何问题，如果是多线程则可能发生线程不安全，需要加上“互斥锁”；在饿汉式中该类的静态方法getInstance()被调用之前，该类的对象已经存在，假设现有两个线程t1 \ t2在调用该方法获取该类的对象，t1 \ t2 无论怎么调用都不会产生新的对象，因为该对象在方法调用之前已经存在，是伴随类的生成而生成。相反，懒汉式对象调用方法getInstance()之前对象不一定存在（至少第一次调用该方法时对象不存在），所以他每次调用之前要检测，若对象不存在则生成对象，对象存在则直接返回。在多线程环境下问题就出现生成对象的时候，假设有两个线程（t1,t2)在调用该方法，考虑这种情况，就是当线程t1检测到该对象不存在的时候，正要准备创建线程（还没创建），而在这个时候CPU切换到t2上执行权交给t2，t2检测到该对象不存在，就生成了对象，t2线程结束了，执行权回到t1上，t1这个时候就不需要判断了，因为开始他判断了的，他就直接向下执行，生成了对象。这样就导致了该类生成了两个不同的对象，当然这种情况不一定会发生，但这种情况是绝对存在的，也许你运行10000次都不会出现，或许你一运行就会出现该问题。所有我们需要对多线程访问的临界资源getInstance()方法加“互斥锁”，保证临界资源线程安全；这表明同一时刻只有一个线程持有该互斥锁，其他线程若要获得该互斥锁访问对象需要等待该线程（持有互斥锁的对象）将其释放。对临界资源getInstance()方法加上互斥锁即需要使用关键字synchronized，如我们使用synchronized修饰方法getInstance()，则每次调用该方法时都需要检测锁，效率不高；其实我们可以这样思考只有在对象被创建的时候我们才上锁，保证对象的唯一，一旦对象都存在了，以后操作还需要锁嘛，不需要了吧，这样我们并得到上面的懒汉式单例模式。

总结：

* 饿汉式：对象预先加载，线程是安全的，在类创建好的同时对象生成，调用获得对象实例的方法反应速度快，代码简练。

* 懒汉式：对象延迟加载，效率高，只有在使用的时候才实例化对象，但若设计不当线程会不安全，代码相对于饿汉式复杂，第一次加载类对象的时候反应不快。

<a href="http://hi.baidu.com/chenbobio/item/9c4ecfa95144fb7b6cd455ca">文章参考</a>