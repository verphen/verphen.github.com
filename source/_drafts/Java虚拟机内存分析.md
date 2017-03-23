Java虚拟机：

堆
	也叫做java 堆、GC堆是java虚拟机所管理的内存中最大的一块内存区域，也是被各个线程共享的内存区域，在JVM启动时创建。该内存区域存放了对象实例及数组(所有new的对象)。其大小通过-Xms(最小值)和-Xmx(最大值)参数设置，-Xms为JVM启动时申请的最小内存，默认为操作系统物理内存的1/64但小于1G，-Xmx为JVM可申请的最大内存，默认为物理内存的1/4但小于1G，默认当空余堆内存小于40%时，JVM会增大Heap到-Xmx指定的大小，可通过-XX:MinHeapFreeRation=来指定这个比列；当空余堆内存大于70%时，JVM会减小heap的大小到-Xms指定的大小，可通过XX:MaxHeapFreeRation=来指定这个比列，对于运行系统，为避免在运行时频繁调整Heap的大小，通常-Xms与-Xmx的值设成一样。


	参考：https://mp.weixin.qq.com/s?__biz=MjM5NzMyMjAwMA==&mid=2651477672&idx=4&sn=ecb128120e301e810f870c50be4149f6&chksm=bd253ad78a52b3c16148b796d8ba7c531d252f67148f467fe5fa186649d0739219e2b86d29ae&mpshare=1&scene=2&srcid=1103ciBfGTbtroggFEeDbgx8&from=timeline&key=60fe7edcfeae255d27b43212320ce8e8dbed000a338e463e3194970f57bfc3b134fcb0b26c887eaea013c2f9c609377341e1c282646db28771a8bc2c0a904ba9f2baa9980d0dee577bb9adb749162b5d&ascene=0&uin=Mjc5OTA0MDUwNQ%3D%3D&devicetype=iMac+MacPro3%2C1+OSX+OSX+10.11.6+build(15G1217)&version=12020010&nettype=WIFI&fontScale=100&pass_ticket=wVlt0F4DX1N494%2B6qh%2F69YYdEi7q59L8B2jyfELdyN4org2KLHp5pN06ViBhTbeM


	http://www.jianshu.com/p/80f5ee32810d