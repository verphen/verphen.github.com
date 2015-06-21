---
title: 线程设计面试题
date: 2013-10-29 23:46:26
categories: java
tags: [java,面试,总结]
---
昨天的关于JAVA Thread的面试题：设计四个线程，其中两个线程对j加1操作，另外两个线程对j减1操作。发现这个面试题网上一大片，我这里也简单地记录一下：
	/**
	 * @author effine
	 * @date 2013-10-28  下午11:50:34
	 */
	
	public class InterviewThread {
	
		private int j = 0;
	
		public static void main(String args[]) {
	
			InterviewThread it = new InterviewThread();
	
			/* 实例化内部类 */
			Inc inc = it.new Inc();
			Dec dec = it.new Dec();
	
			/* 循环得到四个线程 */
			for (int i = 0; i < 2; i++) {
				Thread t = new Thread(inc);
				t.start();
				t = new Thread(dec);
				t.start();
			}
		} //main method finish
	
		/* 同步加1方法 */
		private synchronized void inc() {
			j++;
			System.out.println(Thread.currentThread().getName() + "-inc:" + j);
		}
	
		/* 同步减1方法 */
		private synchronized void dec() {
			j--;
			System.out.println(Thread.currentThread().getName() + "-dec:" + j);
		}
	
		/* 加1线程类 */
		class Inc implements Runnable {
			public void run() {
				for (int i = 0; i < 100; i++) {
					inc();
				}
			}
		}
	
		/* 减1线程类 */
		class Dec implements Runnable {
			public void run() {
				for (int i = 0; i < 100; i++) {
					dec();
				}
			}
		}

	}