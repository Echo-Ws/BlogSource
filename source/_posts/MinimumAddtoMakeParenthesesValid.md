---
title: Minimum Add to Make Parentheses Valid
date: 2018/10/13 23:12:05
tags: medium
categories: [coding,leetcode]
---
# [Description](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/)

Given a string S of '(' and ')' parentheses, we add the minimum number of parentheses ( '(' or ')', and in any positions ) so that the resulting parentheses string is valid.

Formally, a parentheses string is valid if and only if:

It is the empty string, or
It can be written as AB (A concatenated with B), where A and B are valid strings, or
It can be written as (A), where A is a valid string.
Given a parentheses string, return the minimum number of parentheses we must add to make the resulting string valid.

<!--more-->
Example
Input: "()))(("
Output: 4

# My solution:

``` python 3

class Solution:
    def minAddToMakeValid(self, S):
        """
        :type S: str
        :rtype: int
        """
        if len(S)==0:
            return 0
        count=0

        deep=0
        for x in S:
            if x=='(':
                deep+=1
                
            else:
                if deep ==0:
                    count+=1
                else:             
                    deep -=1
              
        return count+deep
    
    
```

# Tricky

```python 3
class Solution(object):
    def minAddToMakeValid(self, S):
        while '()' in S:
            S = S.replace('()', '')
        return len(S)
```

# Analyse
the key is on the balance of parentheses.
there are two cases:
1. the number of '(', l, is more than ')', r.
2. r>l
In the fist case, we need to record l and when meeting ')' just subtract from l. When l become 0 or negative, it means we jump to the second case.
In the second case, we can add the superfluous ‘）’ to the final result because it is impossible to get the corresponding '('. And when it meets '(',it jumps to case 1 again.