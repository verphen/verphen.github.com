title: Try Catch 返回值
tags:
  - try、catch、finally
categories: java
date: 2016-06-15 23:40:22
---

![try catch](http://7xlmfk.com1.z0.glb.clouddn.com/imgs/article/TryCatchFinally.png)

简单分析异常捕获try catch的try和finally中return对结果的影响

<!-- java -->
    
    public class TryCatchTest {

        @Test
        public void testMethod() {
            int i = method1();
            System.out.println(i);
        }

        public int method1() {
            int a = 1;
            try {
                return ++a;
            } catch (Exception e) {
                e.printStackTrace();
            } finally {
                ++a;
            }
            return a;
        }
    }

junit测试打印结果：2
分析：为什么打印的结果是2不是3呢？可以使用debug分析得出，在执行method1方法try中的`++a`之后（a的值为2，同时将返回值2保存到局部变量中），程序并没有立即执行return，而是紧接着执行了finally的`++a`(此时a的值为3)，然后再执行try中的return(返回局部变量中的2)；

若对程序进行改动，在finally中加入return分析返回值是多少？

    public class TryCatchTest {

        @Test
        public void testMethod() {
            int i = method1();
            System.out.println(i);
        }

        public int method1() {
            int a = 1;
            try {
                return ++a;
            } catch (Exception e) {
                e.printStackTrace();
            } finally {
                return ++a;
            }
        }
    }

此时，junit测试打印结果为：3
分析：当程序执行到finally中的`++a` (此时a的值为3)，紧接着执行finally中的return；所以，try和finally中同时出现return时，try中的return将会失效；

