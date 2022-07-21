title: 《Java编程的逻辑》-二进制
categories:
  - 阅读
tags:
  - 阅读
date: 2022-05-26 23:53:06
updated: 2022-05-26 23:53:06
---

  作者：马俊昌
  出版时间：2018年1月

<img src="/imgs/article/programmingLogic4Java.png" alt="Java编程的逻辑" /> 


记录阅读中缺失或遗忘的知识点，强化记忆；

<!-- more -->


。JDK7+提供十进制转换为其他进制方法：

```java
    // 十转换为二进制，结果: 1111011
    Integer.toBinaryString(123);  
    Long.toBinaryString(123L); 

    // 十转换为八进制，结果: 173
    Integer.toOctalString(123); 
    Long.toOctalString(123L); 

    // 十转换为十六进制，结果: 7b
    Integer.toHexString(123); 
    Long.toHexString(123L); 

    // 十转换为指定进制（如十三进制），结果: 96
    Integer.toString(123, 13); 
    Long.toString(123L, 13); 
```

.##### java补码 源码


。按位操作

  位运算有移位运算和逻辑运算。移位有以下几种。
  1）左移：操作符为<<，向左移动，右边的低位补0，高位的就舍弃掉了，将二进制看作整数，左移1位就相当于乘以2。2）无符号右移：操作符为>>>，向右移动，右边的舍弃掉，左边补0。
  3）有符号右移：操作符为>>，向右移动，右边的舍弃掉，左边补什么取决于原来最高位是什么，原来是1就补1，原来是0就补0，将二进制看作整数，右移1位相当于除以2。















