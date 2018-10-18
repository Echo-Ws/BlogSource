---
title: ReverseInteger
date: 2018-10-01 17:12:05
tags: easy
categories: [coding,leetcode]
---
# Description
Given a 32-bit signed integer, reverse digits of an integer.
Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2^31,  2^31 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

<!--more-->
Example
Input: 120
Output: 21

boudary 
input:7463847412 output:2147483647
input:8463847412 output:0
input:-8463847412 output:-2147483648
input:-9463847412 output:0

# my solution:

``` python 3
# 80ms use 1hour 30min
def reverse(self, x):
    """
    :type x: int
    :rtype: int
    """
    # 2^31
    Max = [2,1,4,7,4,8,3,6,4,8]
    if x<0:
        a=-1 
    else:
        a=1
        Max[-1] -=1
        
    x= a*x
    result = []
    num=0
    
    # to remove the 0 in the in end of input
    indicator = True
    
    while x>0:
        
        if indicator and x%10 == 0:
            x = x//10
            continue
        else:
            indicator =False
        
        result.append(x % 10)
        x = x//10
        num +=1
    
    if len(Max)< num:
        return 0
    if len(Max) == num:
        for i in range(num):
            if Max[i]> result[i]:
                break
            if Max[i]== result[i]:
                continue
            return 0
    output=0
    for i in range(num):        
        output += result[i]*(10**(num-1))
        num -=1
    
    return output*a

```

# Best
```python 3
# 48 ms
def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        x = int(str(x)[::-1]) if x >= 0 else - int(str(-x)[::-1])
        return x if x < 2147483648 and x >= -2147483648 else 0
```

# Analyse
对 string 与int 之间的转换不熟悉，对切片操作不熟悉，导致用了大量的计算来造轮子。
时间上用计算好的数据来替代会节约运行时间。