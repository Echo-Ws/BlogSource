---
title: TwoSum
date: 2018-09-18 00:35:31
tags: easy
categories: [coding,leetcode]
---
# description
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.
<!--more-->
Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
# analysis
an array of integers 意味着无序，正负都有可能。无法通过比较target与num的数之间大小关系来减少遍历数。
没有多余的限制条件，故第一反应是暴力搜索Brute Force：
```python
def twoSum(nums, target):
    
    for i in range(len(nums)):
    # 没有说明正负 故下面错误
        # if target>0 & target< nums[i]:
            # continue
        for j in range(i+1, len(nums)):
            if target == (nums[i]+nums[j]):
                return [i, j]  

```
submit：exceed time limitation when the array is large
时间复杂度 n^2
空间复杂度 1
超时，考虑用空间换时间。
此处涉及知识点 hash表 
    当选取一个好的哈希函数时，从哈希表中查询数据的时间代价可以视为1. When a collision occurreds, a look up can degenerate to O(n) time.
通过查找元素是否在哈希表中来减少时间。

# code
```python
def twoSum(nums, target):

    storage = {}
    for i in range( len(nums)):
        if nums[i] not in storage:
            storage[ target- nums[i]] = i
        else:
            return [storage[nums[i]], i]   


```
 

