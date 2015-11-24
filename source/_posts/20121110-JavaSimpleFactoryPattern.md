---
title: JAVA简单工厂模式
date: 2012-11-10 20:13:12
categories: java
tags: [java,设计模式]
---
简单工厂模式 SimpleFactory，又称 静态工厂方法模式（StaticFactory Method）；

* 优点：工厂类是整个模式的关键.包含了必要的逻辑判断，根据外界给定的信息，决定究竟应该创建哪个具体类的对象.通过使用工厂类，外界可以从直接创建具体产品对象的尴尬局面摆脱出来，仅仅需要负责“消费”对象就可以了。而不必管这些对象究竟如何创建及如何组织的．明确了各自的职责和权利，有利于整个软件体系结构的优化。

* 缺点：由于工厂类集中了所有实例的创建逻辑，违反了高内聚责任分配原则，将全部创建逻辑集中到了一个工厂类中；它所能创建的类只能是事先考虑到的，如果需要添加新的类，则就需要改变工厂类了。当系统中的具体产品类不断增多时候，可能会出现要求工厂类根据不同条件创建不同实例的需求．这种对条件的判断和对具体产品类型的判断交错在一起，很难避免模块功能的蔓延，对系统的维护和扩展非常不利；这些缺点在工厂方法模式中得到了一定的克服。

<!-- more -->

* 适用场景：
	1. 工厂类负责创建的对象比较少
	2. 客户只知道传入工厂类的阐述，对于如何创建对象(逻辑)并不关心
	3. 由于简单工厂模式容易违反高内聚责任分配原则，因此一般只在很简单的情况下应用

<a href="http://www.51testing.com/html/64/n-242064.html">（文章参考）</a>

简单工厂模式包含：抽象产品角色、具体产品角色、工厂角色类（有的文章称之为“上帝类”）；下面code包含一个抽象产品类ICar、三个具体产品角色类（奔驰Benz、法拉利Ferrari和捷豹Jaguar）、一个工厂角色类 SimpleFactory 和测试类SimpleFatoryTest.

ICar.java  (抽象产品角色接口)

	/** 
	 * @author effine 
	 * @date 2013年9月10日  上午9:36:19 
	 */  
	  
	package org.effine.simpleFactory;  
	  
	/*抽象产品角色接口：汽车Car*/  
	public interface ICar {  
	  
	    /* 汽车启动 */  
	    public void run();  
	  
	    /* 汽车停止 */  
	    public void stop();  
	}  

Benz.java  (具体产品角色类)

	/** 
	 * @author effine 
	 * @date 2013年9月10日  上午9:38:08 
	 */  
	  
	package org.effine.simpleFactory;  
	  
	/*具体产品角色类：汽车-奔驰Benz*/  
	public class Benz implements ICar {  
	  
	    @Override  
	    public void run() {  
	        System.out.println("奔驰启动");  
	    }  
	  
	    @Override  
	    public void stop() {  
	        System.out.println("奔驰停止");  
	    }  
	}  

Ferrari.java  (具体产品角色类)

	/** 
	 * @author effine 
	 * @date 2013年9月10日  上午9:40:18 
	 */  
	  
	package org.effine.simpleFactory;  
	  
	/*具体产品角色类：汽车-法拉利Ferrari*/  
	public class Ferrari implements ICar {  
	  
	    @Override  
	    public void run() {  
	        System.out.println("法拉利启动");  
	    }  
	  
	    @Override  
	    public void stop() {  
	        System.out.println("法拉利停止");  
	    }  
	}  

Jaguar.java  (具体产品角色类)

	/** 
	 * @author effine 
	 * @date 2013年9月10日  上午9:42:21 
	 */  
	  
	package org.effine.simpleFactory;  
	  
	/*具体产品角色类：汽车-捷豹-Jaguar*/  
	public class Jaguar implements ICar {  
	  
	    @Override  
	    public void run() {  
	        System.out.println("捷豹启动");  
	    }  
	  
	    @Override  
	    public void stop() {  
	        System.out.println("捷豹停止");  
	    }  
	}  

SimpleFactory.java  (工厂角色类)

	/** 
	 * @author effine 
	 * @date 2013年9月10日  上午9:29:02 
	 */  
	  
	package org.effine.simpleFactory;  
	  
	/*工厂角色类*/  
	public class SimpleFactory {  
	  
	    /* 工厂方法，返回类型为抽象的产品角色 */  
	    public static ICar driveCar(String carType) {  
	  
	        /* equalsIgnoreCase() 忽略carType大小写 */  
	        if ("Benz".equalsIgnoreCase(carType)) {  
	            return new Benz();  
	        } else if ("Ferrari".equalsIgnoreCase(carType)) {  
	            return new Ferrari();  
	        } else if ("Jaguar".equalsIgnoreCase(carType)) {  
	            return new Jaguar();  
	        } else {  
	            throw new RuntimeException("没有该汽车类型");  
	        }  
	    }  
	}  

SimpleFactoryTest.java （测试类）

	/** 
	 * @author effine 
	 * @date 2013年9月10日  上午9:48:32 
	 */  
	  
	package org.effine.simpleFactory;  
	  
	/*测试简单工厂方法类*/  
	public class SimpleFactoryTest {  
	    public static void main(String[] args) {  
	  
	        // ICar car = SimpleFactory.driveCar("Benz");  
	        // ICar car = SimpleFactory.driveCar("Ferrari");  
	        ICar car = SimpleFactory.driveCar("Jaguar");  
	  
	        car.run();  
	        car.stop();  
	    }  
	}  