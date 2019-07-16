---
title: Sorting Algorithm
date: 2018/12/12 22:03:57
tags:

categories:
- coding
  

---
Notes for sorting algorithm
<!--more-->
# 插入排序 Insertion Sor
从前建立有序数组，将unsorted 元素不断加入到前面
![插入排序](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)

theta(n^2)
最优 即对以排好序的数组为t heta（n）

stable

# 冒泡排序 Bubble Sort
每次比较相邻的两个数据，将大的移到右边。将有序的数组建立在数组的尾端。

![冒泡排序](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)

theta(n^2)
优化后的冒泡排序在面对排好序的数组的最优情况的是 theta(n)

stable
```
public void bubbleSort(int arr[]) {
    boolean swapped = true;
    for(int i = 0, len = arr.length; swapped && i < len - 1; i++) {
        swapped = false;
        for(int j = 0; j < len - i - 1; j++) {
            if(arr[j + 1] < arr[j]) {
                swap(arr, j, j + 1);
                swapped = true;
            }
        }
    }
}
```
# 选择排序 Selection sort/Maxsort
每次选择unsorted array中最小的element, switch it with the 第一个未排序的元素。

![选择排序](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

比较次数
theta(n^{2})

non-stable ex 5,5,2,4,1 select the smallest number 1, and then swap with the first number 5, we change the order.


# Merge sort
Merge sort is a divide and conquer algorithm 

Worst-case performance	O(n log n)  

Best-case performance	O(n log n) typical, O(n) natural variant  

Average performance	O(n log n)  

Worst-case space complexity	О(n) total with O(n)auxiliary, O(1) auxiliary with linked lists[1]  

![merge sort](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

# Quick sort
选一个基点，把比他小的放一边，比他大的放一边

unstable:  
    ex 1,2,3,4,5,5 select the last number as the spilt number.  
![quick sort](https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)  
Worst-case performance	O(n2)  
Best-case performance	O(n log n) (simple partition)  
or O(n) (three-way partition and equal keys)  
Average performance	O(n log n)  
Worst-case space complexity	O(n) auxiliary (naive)  
O(log n) auxiliary (Sedgewick 1978)  