---
title: JAVA观察者模式
date: 2012-11-08 23:33
categories: java
tags: [java,设计模式]
---
Java观察者模式（Observer Pattern），简单说观察者模式包含四种角色：抽象被观察者角色、抽象观察者角色、具体被观察者角色和具体观察者角色；其中Java本身提供观察者模式的接口供开发者使用，在 java.util包下，包含接口Observer及类Observable，接口Observer是扮演抽象观察者角色，包含一个update()方法，；而类Observable则扮演抽象被观察者角色，开发者只需要继承该类就能很好的运用观察者模式。闲话少说，贴出code供参考：

抽象被观察者角色
<!--lang:java--> 
	/** 
	 * @author Verphen 
	 * @date 2013年10月4日  下午11:02:21 
	 */  
	  
	package org.verphen.observer;  
	  
	/*抽象被观察者角色*/  
	public interface IWitched {  
	  
	    /* 添加观察者 */  
	    public void addWitcher(IWitchers w);  
	  
	    /* 删除观察者 */  
	    public void deleteWitcher(IWitchers w);  
	  
	    /* 被观察者 发生变化，通知观察者 */  
	    public void notifyWitcher(Object o);  
	}  
抽象观察者角色
<!--lang:java-->
	/** 
	 * @author Verphen 
	 * @date 2013年10月4日  下午11:06:57 
	 */  
	  
	package org.verphen.observer;  
	  
	/*抽象观察者角色*/  
	public interface IWitchers {  
	  
	    /* 当被观察者发生变化，接到通知做出反应，更新操作 */  
	    public void update(Object o);  
	}  
具体被观察者角色
<!--lang:java-->
	/** 
	 * @author Verphen 
	 * @date 2013年10月4日  下午11:15:20 
	 */  
	  
	package org.verphen.observer;  
	  
	import java.util.ArrayList;  
	import java.util.List;  
	  
	/*具体被观察者角色*/  
	public class ConcreteWitched implements IWitched {  
	  
	    /* save witchers list */  
	    private List<IWitchers> list = new ArrayList<IWitchers>();  
	  
	    @Override  
	    public void addWitcher(IWitchers w) {  
	        list.add(w);  
	    }  
	  
	    @Override  
	    public void deleteWitcher(IWitchers w) {  
	        list.remove(w);  
	    }  
	  
	    @Override  
	    public void notifyWitcher(Object o) {  
	        for (IWitchers l : list) {  
	            l.update(o);  
	        }  
	    }  
	}  
具体观察者角色
<!--lang:java-->
	/** 
	 * @author Verphen 
	 * @date 2013年10月4日  下午11:16:56 
	 */  
	  
	package org.verphen.observer;  
	  
	/*具体观察者角色*/  
	public class ConcreteWitchers implements IWitchers {  
	  
	    @Override  
	    public void update(Object o) {  
	        System.out.println(o);  
	    }  
	}  
测试类
<!--lang:java-->
	/** 
	 * @author Verphen 
	 * @date 2013年10月4日  下午11:27:18 
	 */  
	  
	package org.verphen.observer;  
	  
	/* observer pattern test class*/  
	public class TestWitch {  
	    public static void main(String[] args) {  
	  
	        /* witched : girl */  
	        IWitched girl = new ConcreteWitched();  
	  
	        /* witchers */  
	        IWitchers witcher1 = new ConcreteWitchers();  
	        IWitchers witcher2 = new ConcreteWitchers();  
	        IWitchers witcher3 = new ConcreteWitchers();  
	  
	        /* witched add witchers */  
	        girl.addWitcher(witcher1);  
	        girl.addWitcher(witcher2);  
	        girl.addWitcher(witcher3);  
	  
	        girl.notifyWitcher(args);  
	    }  
	}  