Java虚拟机：

堆
	也叫做java 堆、GC堆是java虚拟机所管理的内存中最大的一块内存区域，也是被各个线程共享的内存区域，在JVM启动时创建。该内存区域存放了对象实例及数组(所有new的对象)。其大小通过-Xms(最小值)和-Xmx(最大值)参数设置，-Xms为JVM启动时申请的最小内存，默认为操作系统物理内存的1/64但小于1G，-Xmx为JVM可申请的最大内存，默认为物理内存的1/4但小于1G，默认当空余堆内存小于40%时，JVM会增大Heap到-Xmx指定的大小，可通过-XX:MinHeapFreeRation=来指定这个比列；当空余堆内存大于70%时，JVM会减小heap的大小到-Xms指定的大小，可通过XX:MaxHeapFreeRation=来指定这个比列，对于运行系统，为避免在运行时频繁调整Heap的大小，通常-Xms与-Xmx的值设成一样。


	参考：https://mp.weixin.qq.com/s?__biz=MjM5NzMyMjAwMA==&mid=2651477672&idx=4&sn=ecb128120e301e810f870c50be4149f6&chksm=bd253ad78a52b3c16148b796d8ba7c531d252f67148f467fe5fa186649d0739219e2b86d29ae&mpshare=1&scene=2&srcid=1103ciBfGTbtroggFEeDbgx8&from=timeline&key=60fe7edcfeae255d27b43212320ce8e8dbed000a338e463e3194970f57bfc3b134fcb0b26c887eaea013c2f9c609377341e1c282646db28771a8bc2c0a904ba9f2baa9980d0dee577bb9adb749162b5d&ascene=0&uin=Mjc5OTA0MDUwNQ%3D%3D&devicetype=iMac+MacPro3%2C1+OSX+OSX+10.11.6+build(15G1217)&version=12020010&nettype=WIFI&fontScale=100&pass_ticket=wVlt0F4DX1N494%2B6qh%2F69YYdEi7q59L8B2jyfELdyN4org2KLHp5pN06ViBhTbeM


	http://www.jianshu.com/p/80f5ee32810d

	https://my.oschina.net/u/1175007/blog/488886


	通过参数PermSize和MaxPermSize设置永久代的大小

	jdk1.7 将永久代中的字符串常量池移除，放入堆中

	jdk1.8 移除了永久代，目的是Hotspot JVM和JRockit JVM(该虚拟机不存在永久代)相融合的设计思路； 转移位置：将java类部分放到java heap里，将字符串常量和类中的静态变量放到内存里面。类的元数据, 字符串池, 类的静态变量将会从永久代移除, 放入Java heap或者native memory. 其中建议JVM的实现中将类的元数据放入 native memory, 将字符串池和类的静态变量放入Java堆中. 这样可以加载多少类的元数据就不在由MaxPermSize控制, 而由系统的实际可用空间来控制.
为什么这么做呢? 减少OOM只是表因, 更深层的原因还是要合并HotSpot和JRockit的代码, JRockit从来没有一个叫永久代的东西, 但是运行良好, 也不需要开发运维人员设置这么一个永久代的大小.
当然不用担心运行性能问题了, 在覆盖到的测试中, 程序启动和运行速度降低不超过1%, 但是这一点性能损失换来了更大的安全保障.

	参数 MaxMetaspaceSize 允许你来限制用于类元数据的本地内存


永久代(PermGen: Permnent Generation space): 存放类和方法的元数据、以及字符串常量，类被加载是元数据存储在永久代； 是 oracle sun JVM虚拟机 HotSpot 特有的，其他厂商 Oralce JRockit, IBM J9, Taobao JVM 都没永久代；JDK8没有了永久代，当然不会再出现永久代内存溢出(java.lang.OutOfMemoryError: PermGen),取而代之的可能是云空间 metaspace 的其他问题；之前永久代配置参数PermSize(JVM初始分配的非堆内存) 和 MaxPermSize(JVM最大允许分配的非堆内存，按需分配)在JDK8中将被忽略；移除永久代后方法区被存放在元空间metaspace,而字符串常量池则存放java堆；

元数据配置参数：
		-XX:MetaspaceSize 
		-XX:MaxMetaspaceSize 
		-XX:MinMetaspaceFreeRatio 
		-XX:MaxMetaspaceFreeRatio