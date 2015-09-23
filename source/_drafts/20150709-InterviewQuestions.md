title: "InterviewQuestions"
date: 2015-07-09 15:50:01
categories: web
tags:
  - interview
  - 总结
---

java什么时候会发生内存溢出

	内存溢出，是由于内存(内存是堆么?)中没有被引用的对象(垃圾)太多而JVM回收机制没有及时回收; 
	可能出现的场景：程序出现死循环，一直在创建没有引用的对象;递归调用；大量循环或死循环;全局变量过多;数组、List、Map数据过大;频繁的进行字符串的拼接操作；
	

4. 数据库索引是否有顺序需求，索引index(age,name,date,address)适合那些sql语句（AB）
   A. select * from student where age =? and name=? and  date=? and address=?
   B. select * from student where age =? and name=?
   C. select * from student where  date=? and address=?
   D. select * from student where address=?



数据库查询
     表A： 学生
     表B： 课程
     表C： 学生课程关联
     问题1：查询选择所有课程的学生
     问题2：查询选择课程超过5门以上的学生

     -- the one
select u.id, u.name
from user u,
     (
          select uid from user_course uc group by uid having count(*) = (select count(*) from course)
         
      ) temp
where u.id = temp.uid

-- the two
select u.id, u.name
from user u
where u.id in
    (
        select uid from user_course uc group by uid having count(*) = (select count(*) from course)
             
    )



猴子一天摘了n个苹果，第一天吃了一半再多吃1个，第二天再吃剩余的苹果的一半再多吃1个，以此类推，第10天只剩1个苹果，程序实现，猴子摘了多少个苹果?

      public static void main(String[] args) {
             int sum = 1;
             for( int i=9; i >= 1; i--){
                   sum = ( sum+1)*2;
            }
            System. out.println(sum);
      }


tag: 数据库大数据时，用程序维护主外键；小数据时用数据库维护主外键;
	 不建议创建外键：由程序维护数据的一致性和唯一性
	http://www.iteye.com/problems/91638
