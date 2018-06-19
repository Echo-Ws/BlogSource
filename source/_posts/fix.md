---
title: 维修记录
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
1. 从官网下载iso，用ultraiso写入，出现
INF file txtsetup.sif is corrupt or missing,status 18
解决方法看youtube这个[视频](https://www.youtube.com/watch?v=BjPnAR12eIc)
具体说
将txtsetup.sif从i386文件夹中复制到上级目录里，即和i386同级。
将i386改名为 $WIN_NT$.~BT 
即可解决。

安装的时候出现了：请将光盘放在光驱中。

建议使用WinSetupFromUSB制作u盘
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
