title: Integer的对等比较
tags:
  - java
  - Integer
categories: java
date: 2015-06-22 17:38:25
---
分析之前，先猜想一下看看下面code snippets的输出：

	package cn.effine.test;

	public class IntegerTest {
		
		public static void main(String[] args) {
			
			Integer i1 = 2;
			Integer i2 = 2;
			System.err.println("i1 == i2 : " + (i1 == i2));
			
			Integer i3 = new Integer(2);
			Integer i4 = new Integer(2);
			System.err.println("i3 == i4: " + (i3 == i4));
			
			Integer i5 = 128;
			Integer i6 = 128;
			System.err.println("i5 == i6 : " + (i5 == i6));
			System.err.println("i5、i6的inValue()方法等值比较： " + (i5.intValue() == i6.intValue()));
			System.err.println("i5、i6的equals的比较： " + i5.equals(i6));

		}
	}

<!-- more-->

运行结果：

	i1 == i2 : true
	i3 == i4: false
	i5 == i6 : false
	i5、i6的inValue()方法等值比较： true
	i5、i6的equals的比较： true

如果你对某些输出感到诧异，接着往下看我的分析：

初始化Integer声明的变量时，会去调用Integer.valueOf()方法进行处理；方法源码如下

    public static Integer valueOf(int i) {
        assert IntegerCache.high >= 127;
        if (i >= -128 && i <= 127)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);
    }

至于为什么调用该方法进行if判断？可能是因为8位二进制的范围是-128到127；当传入的参数在该范围则返回int原始数据类型，超出该范围则新建一个Integer对象，对象的对等比较（“==”）比较的是对象的内存地址；现在你再回去过看程序：

初始化i1、12时，调用Integer.valueOf()方法，由于i1\i2的值(2)在-128到127范围内，方法返回int类型的值2，进行对等比较时则返回ture

声明i3、i4时，默认新建了个Integer对象，所以对等比较的是两个对象的内存地址，因此返回false

初始化i5、i6时，调用Integer.valueOf()方法，其值-128在127范围外，所以方法返回新建的Integer对象，进行对等比较返回false

调用Integer.intValue()方法返回的是对应对象int值，i5、i6的方法返回值都是128，对等比较当然返回true

Integer对象的equals()方法底层调用的是Integer.intValue()方法，对等比较同样比较其int值，返回同样为true