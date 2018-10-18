---
title: RomanToInteger
date: 2018-10-08 15:44:19
tags: easy
categories: [coding,leetcode]
---
# Description
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

[detail](https://leetcode.com/problems/roman-to-integer/)
<!--more-->
# My
```python
class Solution:
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        dic = {'I':1,'V':5,'X': 10,'L':50,'C':100,'D':500,'M':1000}
        pre = 0
        result=0
        
        for i in range(len(s)):
            if not pre:
                pre = dic[s[i]]
                continue
            
            if dic[s[i]]<= pre:
                result += pre
                pre = dic[s[i]]
            else:
                result= result+dic[s[i]]-pre
                pre =0
            
        result+=pre
        return result    
            
    
    def test(self):
        print(self.romanToInt("IV"))
        print(self.romanToInt("I"))
        print(self.romanToInt("MCMXCIV"))


        
        
```

# Best
``` python
d = {'M':1000, 'D':500, 'C':100, 'L':50, 'X':10, 'V':5, 'I':1}

def romanToInt(self, s):
    res, p = 0, 'I'
    for c in s[::-1]:
        res, p = res - d[c] if d[c] < d[p] else res + d[c], c
    return res
```

# Analyse
倒序的优势在于我们可以直接判定是加还是减当前的数，而不需要在多读后面的数来判断。