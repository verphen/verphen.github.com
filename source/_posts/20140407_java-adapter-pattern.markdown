---
title: JAVA适配器模式
date: 2014-04-07 23:00:06
categories: java
tags: [java,设计模式]
---
适配器模式（Adapter Pattern）：把类的接口变换成客户端所期待的另一种接口，从而使原本因接口不匹配而无法再一起工作的两个类一起工作。

适配器模式的两种形式：

1. 类的适配器模式：把被适配的类的API转换成目标类的API；该模式涉及的角色：

	- 目标（Target）角色：这就是所期待得到的接口；**注意，这里讨论的是类的适配器模式，因此目标不可以是类。**
		
			/**
			 * @author effine
			 * @date 2014年4月7日   下午11:44:58
			 */
			
			package org.effine.adapter;
			
			/* 目标角色 */
			public interface Target {
				
				/**
				 * 这是源类（客户端类）也有的方法method1()
				 */
				void method1();
				
				/**
				 * 这是源类（客户端类）没有的方法method2()
				 */
				void method2();
			}
	- 源（Adaptee）角色：现有需要适配的接口
			<!--lang:java--->
		
			/**
			 * @author effine
			 * @date 2014年4月7日   下午11:49:00
			 */
			
			package org.effine.adapter;
			
			/* 源角色 */
			public class Adaptee {
			
				/**
				 * 源类（客户端类）含有方法method1()
				 */
				public void method1() {
					/* method body */
				}
			}
	- 适配器（Adapter）角色：适配器类是本模式的核心；适配器把源接口转换成目标接口；显然，这一角色不可能是接口，必须是类。
		    	<!--lang:java--->
			
			/**
			 * @author effine
			 * @date 2014年4月7日   下午11:48:30
			 */
			
			package org.effine.adapter;
			
			/* 类的适配器角色 */
			public class CalssAdapter extends Adaptee implements Target {
			
				/**
				 * 由于源类（客户端类）没有方法method2(),因此适配器补上该方法
				 */
				public void method2() {
					/* method body */
				}
			}

	类适配器的效果：使用一个具体的类把源（Adaptee）适配到目标（Target）中，这样一来源及源的子类都使用此类适配器，就行不通（使用该适配器即可以：`Adaptee adapee = new ClassAdapter();`）。由于适配器类是源类的子类，因此适配器类可以重写（覆盖）源类的一些方法。且只引进一个适配器类，因此只有一个线路能到达目标类，使问题得到简化。

2. 对象的适配器模式：与类的适配器模式一样，都是把被适配的类的API转换成目标类的API；区别在于，对象的适配器模式不是使用继承关系连接到Adaptee类，而是使用委托关系进行连接。

	- 目标（Target）角色：这就是所期待得到的接口,**目标可以是具体或抽象的类**。code如类适配器模式的目标角色。
	
	- 源（Adaptee）角色：现有需要适配的接口；code如类适配器模式的源角色。

	- 适配器（Adapter）角色：适配器类是本模式的核心；适配器把源接口转换成目标接口；显然，这一角色不可能是接口，必须是类。
			<!--lang:java-->
			
			/**
			 * @author effine
			 * @date 2014年4月8日   上午12:20:12
			 */
			
			package org.effine.adapter;
			
			/* 对象的适配器角色 */
			public class ObjectAdapter implements Target {
			
				private Adaptee adaptee;
			
				public ObjectAdapter(Adaptee adaptee) {
					super();
					this.adaptee = adaptee;
				}
			
				/**
				 * 源类（客户端类）的方法method1(),适配器直接委派即可
				 */
				public void method1() {
					adaptee.method1();
				}
			
				/**
				 * 由于源类（客户端类）没有方法method2(),因此适配器补上该方法
				 */
				public void method2() {
					/* method body */
				}
			
			}
	
		对象的适配器的效果：一个适配器可以把多个不同的源适配到同一个目标，换而言之，同一个适配器可以把源类和它的子类都适配到目标接口。与类的适配模式相比，想要置换（重写，覆盖）源类的方法则不易，如必须实现则可以先做一个源类的子类，该子类重写父类（源类）的方法，然后将源类的子类作为对象适配器的真正源进行适配；这样也方便添加新的方法（子类中实现），且添加的方法可同时适合所有的源。