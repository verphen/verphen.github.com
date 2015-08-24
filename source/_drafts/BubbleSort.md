title: 冒泡排序
date: 2015-08-14 20:37:54
categories: algorithm
tags:
  - Algorithm
  - mysql
---


ps: code from baike.baidu.com
public class BubbleSort
{
    public void sort(int[] a)
    {
        int temp = 0;
        for (int i = a.length - 1; i > 0; --i)
        {
            for (int j = 0; j < i; ++j)
            {
                if (a[j + 1] < a[j])
                {
                    temp = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = temp;
                }
            }
        }
    }
}