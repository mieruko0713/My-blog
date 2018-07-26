---
title: 算法笔记：排序
date: 2017-06-10
tags: ["算法"]
---

## 前言
~~算法系列不需要前言~~    
本系列力求以尽可能简洁的语言对传统算法作可理解的描述，不贴代码/伪代码。    
不是错题本，不是OJ参考答案(这个在[这里](https://github.com/mieruko0713/mieruko_algorithms))，只是总结   
      
先上图：     
![算法](http://7xl4oh.com1.z0.glb.clouddn.com/%E7%AE%97%E6%B3%95.png)

## 冒泡排序(O(n^2))
冒泡排序的思想就是通过与相邻元素的比较和交换来把大的数交换到最后面。     

## 选择排序(O(n^2))
首先在未排序序列中找到最小元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小元素，然后放到排序序列第二位。以此类推，直到所有元素均排序完毕。

## 插入排序(O(n^2)) 
步骤：    
- 从第一个元素开始，该元素可以认为已经被排序
- 取出下一个元素，在已经排序的元素序列中从后向前扫描
- 如果该元素（已排序）大于新元素，将该元素移到下一位置
- 重复步骤3，直到找到已排序的元素小于或者等于新元素的位置
- 将新元素插入到该位置中
- 重复步骤2

## 快速排序(不稳定的，平均时间复杂度O(nlogn))
冒泡+二分+递归分治    
其思想是来自冒泡排序，冒泡排序是通过相邻元素的比较和交换把最大的冒泡到最末端，而快速排序是比较和交换小数和大数，这样一来不仅把小数冒泡到上面同时也把大数沉到下面。
步骤:   
- 从数列中挑出一个元素，称为 “基准”（pivot）
- 重新排序数列，所有元素比基准值小的摆放在基准前面，所有元素比基准值大的摆在基准的后面（相同的数可以到任一边）。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作。
- 递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序

## 归并排序（稳定，平均时间复杂度O(nlogn),空间复杂度O(n)）
归并排序使用了递归分治的思想。   
其基本思想是，先递归划分子问题，然后合并结果。   
把待排序列看成由两个有序的子序列，然后合并两个子序列，然后把子序列看成由两个有序序列。。。。。倒着来看，其实就是先两两合并，然后四四合并。。。最终形成有序序列。空间复杂度为O(n)，时间复杂度为O(nlogn)。

## 堆排序（时间复杂度nlogn）
首先，实现堆排序需要解决两个问题：

1. 如何由一个无序序列键成一个堆？   
可以直接使用线性数组来表示一个堆，由初始的无序序列建成一个堆就需要自底向上从第一个非叶元素开始挨个调整成一个堆。

2. 如何在输出堆顶元素之后，调整剩余元素成为一个新的堆？     
怎么调整成堆？首先是将堆顶元素和最后一个元素交换。然后比较当前堆顶元素的左右孩子节点，因为除了当前的堆顶元素，左右孩子堆均满足条件，这时需要选择当前堆顶元素与左右孩子节点的较大者（大顶堆）交换，直至叶子节点。我们称这个自堆顶自叶子的调整成为筛选。  
  
## 希尔排序(时间复杂度n^1.3)   
插入排序的改进版本    
先将整个待排记录序列分割成为若干子序列分别进行直接插入排序，待整个序列中的记录基本有序时再对全体记录进行一次直接插入排序。

## 基数排序
基数排序是一种借助多关键字排序思想对单逻辑关键字进行排序的方法。所谓的多关键字排序就是有多个优先级不同的关键字。比如说成绩的排序，如果两个人总分相同，则语文高的排在前面，语文成绩也相同则数学高的排在前面。。。如果对数字进行排序，那么个位、十位、百位就是不同优先级的关键字，如果要进行升序排序，那么个位、十位、百位优先级一次增加。基数排序是通过多次的收分配和收集来实现的，关键字优先级低的先进行分配和收集。