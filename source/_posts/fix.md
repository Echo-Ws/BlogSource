---
title: 搞机记录
date: 2018-06-04 21:11:37
tags:
    - xp
categories: 维修
---
computer science = 修电脑
<!--more-->
# 问题描述
>Haier 系列笔记本，xp系统。
每次开机做硬盘检查，且会检查到未知的新硬件，不久会自动卡死蓝屏。
听声音感觉硬盘卡碟严重，然而使用安全模式不会自动重启，硬盘访问正常，可以排除硬件问题。据使用者描述曾删除c盘文件，先重装电脑排除软件原因。

# 装机记录
1. 使用UltraISO制作的u盘启动装ghost系统，出现
Error:cannot load file (code:5555h):\boot\AUTO.ini 
建议使用DiskGenius重建MBR引导，无效。
2. 进入winpe，出现
could not find ntldr

问题可能出在ghost系统或者ultraiso上。

3. 从官网下载iso，用ultraiso写入，出现
INF file txtsetup.sif is corrupt or missing,status 18
解决方法看youtube这个[视频](https://www.youtube.com/watch?v=BjPnAR12eIc)
具体说
将txtsetup.sif从i386文件夹中复制到上级目录里，即和i386同级。
将i386改名为 $WIN_NT$.~BT 
即可解决。

安装的时候出现了：请将光盘放在光驱中。无解放弃。

建议使用WinSetupFromUSB制作u盘。

4. 官网下载WinSetupFromUSB皆显示无资源。无奈从第三方下载：1.8汉化版，在写入镜像时出现error，不知道代码无法解决。在csdn上找到1.7，写入时巨慢。
成功启动且进入装机界面，在安装的时候出现复制错误，找不到文件，怀疑自己的u盘 有问题，换16g的 新u盘重新做。然而无法分出新区安装ntldr。
解决方法1 diskgenu备份旧u的隐藏分区，在克隆的新u。
2将旧电脑硬盘拿下来单独装系统。等读卡器拿回来在尝试。

用windows7 usb dvd工具
出现过
irq less or qual
memory management
且有时可以开机有时不行，怀疑是硬件问题，但是不知道是内存还是硬盘还是主板。
尝试换装win10

全部在写入的时候出错，怀疑内存或硬盘出错。

将机子的硬盘装在本人的笔记本，成功安装win10，排除硬盘问题。然而win10的引导项目不是直接装在硬盘里，好像装在了主板上？导致我换回原来的硬盘时出现了新的引导项。
将硬盘装回旧机，引导项目丢失，期望通过u盘修复，然而无法进入U盘，显示有错误，怀疑其他硬件的问题导致。然而没有ddr2的内存测试，无法确定出错的硬件。


-----
家里还有一台闲置的FUJITSU S2110，之前还原了原版英文系统。
需要安装中文版

将下载好的xp86 解压到U盘里，直接在系统里打开，安装，成功。证明下载文件没有问题。
安装了一个纯净系统，需要自己装驱动。
[fujitsu 官方驱动下载地址](http://www.fujitsu.com/cn/support/products/computing/pc/#)

---

# 备份旧电脑数据
方案：
1.局域网互传，需要两台电脑同时开启。win10设共享文件夹，xp访问将数据拷贝进去，速度约1.2mB/s。没有深究瓶颈。
2.硬盘拷贝。3t移动硬盘 GPT分区，32位xp上无法识别，需使用MBR分区表。在MBR分区表中，一个分区最大的容量为2T，且每个分区的起始柱面必须在这个disk的前2T内。

对分区没有什么特别的想法，但已经拷了近300G的数据，不想在此格式化。使用旧的硬盘进行数据的迁移。
[关于GPT和MBR的科普](https://blog.csdn.net/z15732621736/article/details/49046367)

---
# 相片管理 
参考:
[如何高效地整理照片及管理照片？ - 赵晗的回答 - 知乎](https://www.zhihu.com/question/20966524/answer/28839224)
选择 [Lightroom 5.7](http://www.downza.cn/soft/19598.html), 注册码1160-4102-9128-2011-2993-5806 注:断网操作
主要使用功能：关键词标注