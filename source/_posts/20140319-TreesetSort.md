---
title: TreeSet排序
date: 2014-03-19 00:18:30
categories: java
tags: [java,算法]
---
TreeSet 是 SortedSet 接口（Set接口的子接口）的实现类，该类的内部实现了排序；因此，TreeSet 可以给Set集合中的元素进行指定方式的排序，保证元素唯一性的方式：通过比较结果是否为0，底层数据结构为“二叉树”。

**排序的第一种方式：**元素自身具备比较性。只要让元素实现Comparable接口，覆盖compareTo()方法即可

<!-- more -->

测试类：TreeSetDemo.java

	import java.util.SortedSet;
	import java.util.TreeSet;
	
	public class TreeSetDemo {
	
		public static void main(String[] args) {
	
			SortedSet<Teacher> ss = new TreeSet<Teacher>();
	
			ss.add(new Teacher("lisi", 30));
			ss.add(new Teacher("wangwu", 20));
			ss.add(new Teacher("zhangsan", 40));
			ss.add(new Teacher("wanger", 32));
			ss.add(new Teacher("lida", 10));
	
			System.out.println(ss);
		}
	}	

实现 Comparable 接口类：Teacher.java

	//同姓名同年龄的学生视为同一个学生，按照学生的年龄排序
	public class Teacher implements Comparable {
	
		private String name;
		private int age;
	
		public Teacher(String name, int age) {
			this.name = name;
			this.age = age;
		}
	
		public String getName() {
			return name;
		}
	
		public void setName(String name) {
			this.name = name;
		}
	
		public int getAge() {
			return age;
		}
	
		public void setAge(int age) {
			this.age = age;
		}
	
		//排序的操作方法，下面的操作为按照年龄的升序排序
		@Override
		public int compareTo(Object o) {
			Teacher t = (Teacher) o;
			int num = new Integer(this.age).compareTo(new Integer(t.age));
			return num == 0 ? this.name.compareTo(t.name) : num;
		}
	
		@Override
		public String toString() {
			return name + ":" + age;
		}
	}
	
**排序的第二种方式：**元素自身不具备比较性，或者元素自身的可比较性不是所需要的；此时定义另外的类实现Comparator接口，覆盖其Compare()方法，将该Comparator接口子类对象作为实际参数传递给TreeSet集合的构造方法，该对象就是比较器。

定义额外比较器的类：ComparatorDemo.java

	import java.util.Comparator;
	
	//比较器类实现Comparator接口
	public class ComparatorDemo implements Comparator {
	
		@Override
		public int compare(Object o1, Object o2) {
	
			Teacher t1 = (Teacher) o1;
			Teacher t2 = (Teacher) o2;
	
			int num = t1.getName().compareTo(t2.getName());
			//此处运用了问号表达式
			return num == 0 ? 
				new Integer(t1.getAge()).compareTo(new Integer(t2.getAge())) : num;
		}
	
	}

修改测试类代码：TreeSetDemo.java

	import java.util.SortedSet;
	import java.util.TreeSet;
	
	public class TreeSetDemo {
	
		public static void main(String[] args) {
	
			//将Comparator实现类作为TreeSet的构造参数
			SortedSet<Teacher> ss = new TreeSet<Teacher>(new ComparatorDemo());
	
			ss.add(new Teacher("lisi", 30));
			ss.add(new Teacher("wangwu", 20));
			ss.add(new Teacher("zhangsan", 40));
			ss.add(new Teacher("wanger", 32));
			ss.add(new Teacher("lida", 10));
	
			System.out.println(ss);
		}
	}
实现 Comparable 接口的类（Teacher.java）保持不变即可。