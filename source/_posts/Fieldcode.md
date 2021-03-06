---
title: Fieldcode
date: 2018-05-16 15:24:59
tags: 
    - word 
    - 域代码
categories: windows
---

# 需求描述
毕业论文格式要求大标题采用“第一章”的汉字多级标题格式，而对于公式，图，表等标号需要按章节编号，如1.1 2.3.3等。如果直接使用题注进行标注会产生“一.1”的效果。对此要使用自动标号必须的用到word里域代码的相关知识。

此外域代码还能在表格中像excel中用引用相对位置进行计算，使表格填写更加高效。
然而网上相关资料着实是少，官方文档缺少实例，故写本文做一个域代码的学习记录。
# 系统环境
win10， word2016

<!--more-->


# 语法说明
域代码出现在大括号 ( { } ) 内。其中{ }不是用键盘上的{ }输入的，而是按Ctrl+F9。形式如
{ 域名称 指令 可选开关 }。不同的命令可以在[参考资料3](https://support.office.com/zh-cn/article/word-%E4%B8%AD%E7%9A%84%E5%9F%9F%E4%BB%A3%E7%A0%81%E5%88%97%E8%A1%A8-1ad6d91a-55a7-4a8d-b535-cf7888659a51)中找到。

域代码决定域中显示的内容。计算域代码后文档中显示的为域结果。要在查看域代码和域代码结果之间切换，请按 Alt+F9。
*注意：*
- 每次输入完一条命令后切记要Ctrl+A, F9来更新全文域，不然很容易出现显示为空或着错误的情况。
- 在输入命令时要注意符号是否是英文，中文字符可能造成语法错误。

要实现自动标号和表格相对位置主要是利用 Seq域。

## Seq域实现公式标号

语法：
<center>{ SEQ 标识符 [书签 ] [开关 ] }</center>
标识符可以理解为自定义的变量名。默认从1开始计数，随后每使用一次值自增1.
比如在第一张的标题后面输入{ SEQ chap}。此时即创造了值为1的变量chap。在第二章标题后面同样输入{ SEQ chap}，此时chap自增为2。
然而我们在标题出不需要阿拉伯标号，故使用开关\h将其隐藏。最终在标题后输入：{ SEQ chap \h}

在需要用到的章节标号处使用\c，表示重复前边最近的序列号。而对于公式或图标的(章节-公式号）的标记形式，只需要对公式、图、表分别创建新的seq变量来计数即可。
比如最终公式标号的域代码可以写为：
<center>( { SEQ chap \c }-{ SEQ equ } )</center>

然而对于新的章节公式要重新标号，此时就要用\r n 将变量重置为n这个指定的数字，缺省n时默认为1。 例如，{ SEQ figure \r 3 } 从 3 开始图表编号。故只需要在新的章节任意一个早于标号的地方，比如标题处，输入域代码重置即可。以上述公式标号变量的equ为例，在标题处输入{ SEQ equ \r \h}即可。

还没有弄图床，全是文字略显抽象，具体表现效果可以参照[参考资料2](https://support.office.com/zh-cn/article/word-%E4%B8%AD%E7%9A%84%E5%9F%9F%E4%BB%A3%E7%A0%81%E5%88%97%E8%A1%A8-1ad6d91a-55a7-4a8d-b535-cf7888659a51)

# 表格实现相对位置计算
word中的表格不能象Excel一样实现相对引用。对于大量的表格计算，常规的做法是先写一个公式，然后复制到其他单元格，最后再逐个修改。而seq域可以实现自增，实现一个公式完成同一种运算。

## 思路
假设有表格：(切记空一行否者无法正确渲染出表格)

| 特征 | d1 | d2 | d3|sum
|:-:|:-:|:-:|:-:|:-:
| a | 1 | 2| 3|x|
|b |1|2 |3| |
| c | 1 | 2 |3| |
|avg| y | | | | |

### 求x：
一般公式写成 {：= sum(B2:D2)}
不同行之间的区别在于序号，故可以用seq变量来实现自增。由于加入了域代码，要用quote来实现。且从2开始计算，一种方法时对变量加1：
<center>{ ={ quote "sum(B{ ={ seq Col_A }+1 }:D{ ={ seq Col_A \c}+1})" } }</center>


### 求y：
一般公式写成 {：= average(B2:B4)}
不同列之间字母不同，可以用seq的\*alphabetic开关，把数字转化为字母。此时无法通过先加1在转为字母实现从B开始计算，只能通过表头先写变量{ seq Row_A \r 1 }解决。

<center>{ ={ quote "average({ seq Row_A \*alphabetic }2:{ seq Row_A \r \*alphabetic }4)" } }</center> 




# 参考资料
1. [含章节号的题注编号以阿拉伯数字显示](https://blog.csdn.net/buaazt/article/details/70257619)
2. [文1的完善](http://www.cnblogs.com/partlycloudy/p/7427496.html)
3. [office 域代码的官方文档](https://support.office.com/zh-cn/article/word-%E4%B8%AD%E7%9A%84%E5%9F%9F%E4%BB%A3%E7%A0%81%E5%88%97%E8%A1%A8-1ad6d91a-55a7-4a8d-b535-cf7888659a51)
4. [office word表格中使用公式的官方文档](https://support.office.com/zh-cn/article/%E5%9C%A8-word-%E6%88%96-outlook-%E8%A1%A8%E6%A0%BC%E4%B8%AD%E4%BD%BF%E7%94%A8%E5%85%AC%E5%BC%8F-cbd0596e-ea8a-485e-a35d-b2cb2c4f3e27)
5. [如何实现用域对Word表格的相对引用和自动计算？](https://jingyan.baidu.com/article/63f2362817706d0209ab3d72.html)