---
title: Java守护线程
date: 2013-10-15 01:20:22
categories: java
tags: [java,总结]
---
在Java中有两类线程：User Thread(用户线程)、Daemon Thread(守护线程)

* Daemon的作用是为其他线程的运行提供便利服务，比如垃圾回收线程就是一个很称职的守护者。User和Daemon两者几乎没有区别，唯一的不同之处就在于虚拟机的离开：如果 User Thread已经全部退出运行了，只剩下Daemon Thread存在了，虚拟机也就退出了。 因为没有了被守护者，Daemon也就没有工作可做了，也就没有继续运行程序的必要了。值得一提的是，守护线程并非只有虚拟机内部提供，用户在编写程序时也可以自己设置守护线程。下面的方法就是用来设置守护线程的。`public final void setDaemon(boolean on)`

<!-- more -->

这里有几点需要注意： 

1. thread.setDaemon(true)必须在thread.start()之前设置，否则会跑出一个IllegalThreadStateException异常。你不能把正在运行的常规线程设置为守护线程
2. 在Daemon线程中产生的新线程也是Daemon的
3. 不要认为所有的应用都可以分配给Daemon来进行服务，比如读写操作或者计算逻辑。因为你不可能知道在所有的User完成之前，Daemon是否已经完成了预期的服务任务。一旦User退出了，可能大量数据还没有来得及读入或写出，计算任务也可能多次运行结果不一样。这对程序是毁灭性的。造成这个结果理由已经说过了：一旦所有User Thread离开了，虚拟机也就退出运行了。
 
<!--lang:java-->
	import java.io.*;     
	    
	//完成文件输出的守护线程任务  
	class TestRunnable implements Runnable{     
	    public void run(){     
	               try{     
	                  Thread.sleep(1000);//守护线程阻塞1秒后运行     
	                  File f=new File("daemon.txt");     
	                  FileOutputStream os=new FileOutputStream(f,true);     
	                  os.write("daemon".getBytes());     
	           }     
	               catch(IOException e1){     
	          e1.printStackTrace();     
	               }     
	               catch(InterruptedException e2){     
	                  e2.printStackTrace();     
	           }     
	    }     
	}     
	public class TestDemo2{     
	    public static void main(String[] args) throws InterruptedException     
	    {     
	        Runnable tr=new TestRunnable();     
	        Thread thread=new Thread(tr);     
	                thread.setDaemon(true); //设置守护线程     
	        thread.start(); //开始执行分进程     
	    }     
	}     
	//运行结果：文件daemon.txt中没有"daemon"字符串。  
看到了吧，把输入输出逻辑包装进守护线程多么的可怕，字符串并没有写入指定文件。原因也很简单，直到主线程完成，守护线程仍处于1秒的阻塞状态。这个时候主线程很快就运行完了，虚拟机退出，Daemon停止服务，输出操作自然失败了。
 
例子2 ： 
<!--lang:java-->
	public class Test {
		public static void main(String args) {
			Thread t1 = new MyCommon();
			Thread t2 = new Thread(new MyDaemon());
			t2.setDaemon(true); // 设置为守护线程
			t2.start();
			t1.start();
		}
	}
	
	class MyCommon extends Thread {
		public void run() {
			for (int i = 0; i < 5; i++) {
				System.out.println("线程1第" + i + "次执行！");
				try {
					Thread.sleep(7);
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
		}
	}
	
	class MyDaemon implements Runnable {
		public void run() {
			for (long i = 0; i < 9999999L; i++) {
				System.out.println("后台线程第" + i + "次执行！");
				try {
					Thread.sleep(7);
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
			}
		}
	} 
    
	后台线程第0次执行！ 
	线程1第0次执行！ 
	线程1第1次执行！ 
	后台线程第1次执行！ 
	后台线程第2次执行！ 
	线程1第2次执行！ 
	线程1第3次执行！ 
	后台线程第3次执行！ 
	线程1第4次执行！ 
	后台线程第4次执行！ 
	后台线程第5次执行！ 
	后台线程第6次执行！ 
	后台线程第7次执行！ 
	Process finished with exit code 0 

从上面的执行结果可以看出：前台线程是保证执行完毕的，后台线程还没有执行完毕就退出了。实际上：JRE判断程序是否执行结束的标准是所有的前台执线程行完毕了，而不管后台线程的状态，因此，在使用后台县城时候一定要注意这个问题。实际应用例子：在使用长连接的comet服务端推送技术中，消息推送线程设置为守护线程，服务于ChatServlet的servlet用户线程，在servlet的init启动消息线程，servlet一旦初始化后，一直存在服务器，servlet摧毁后,消息线程自动退出 

容器收到一个Servlet请求，调度线程从线程池中选出一个工作者线程,将请求传递给该工作者线程，然后由该线程来执行Servlet的 service方法。当这个线程正在执行的时候,容器收到另外一个请求,调度线程同样从线程池中选出另一个工作者线程来服务新的请求,容器并不关心这个请求是否访问的是同一个Servlet.当容器同时收到对同一个Servlet的多个请求的时候，那么这个Servlet的service()方法将在多线程中并发执行。

Servlet容器默认采用单实例多线程的方式来处理请求，这样减少产生Servlet实例的开销，提升了对请求的响应时间，对于Tomcat可以在server.xml中通过<Connector>元素设置线程池中线程的数目。 