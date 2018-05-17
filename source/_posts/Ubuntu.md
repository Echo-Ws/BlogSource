---
layout: 
title: Record for Ubuntu
date: 2018-05-17 22:39:04
tags: 
    - 装机
    - 备忘
categories: Ubuntu
---

我的ubuntu 16.04使用记录，以备未来重装电脑。
# Details
Intel® Core™ i7-4710MQ CPU @ 2.50GHz × 8 
GeForce GTX 860M/PCIe/SSE2
<!--more-->
# 装机记录
1. 制作引导盘　　　　　
    UltraISO做启动U盘时的选项：
    刻录校验：打上对号
    写入方式：USB-ZIP+
    便捷启动：写入新的硬盘主引导记录（MBR）-USB-ZIP+
    设置完毕后，单击“写入”
    参考：[百度经验](http://jingyan.baidu.com/article/60ccbceb18624464cab197ea.html)　
2. [更换软件源](http://www.10tiao.com/html/346/201607/2651089764/1.html)
3. 显卡驱动
   - 已经安装了nvidia361的话
    ```shell
    sudo apt purge nvidia-361
    sudo apt-add-repository ppa:graphics-drivers/ppa -y
    sudo apt update
    sudo apt install nvidia-364
    ```
    - 如果还没安装nvidia驱动直接
    ```shell
    sudo add-apt-repository ppa:graphics-drivers/ppa
    sudo apt update
    ```
    从[nvida官网](http://www.nvidia.cn/Download/index.aspx?lang=cn)查询对应显卡对应的驱动 替代命令中的版本号

    sudo apt install nvidia-364 nvidia-settings nvidia-prime
    参考：
    + [登陆界面无限重启](https://www.v2ex.com/t/275534)
    + [Ubuntu 16.04 安装英伟达（Nvidia）显卡驱动](https://gist.github.com/dangbiao1991/7825db1d17df9231f4101f034ecd5a2b) 
4. [自动挂载硬盘](http://blog.sina.com.cn/s/blog_142e95b170102vx2a.html)
## software
1. Download tool:
    [uget+aria2](http://blog.csdn.net/xiaohouye/article/details/54603198)
    ```shell
    sudo apt-get install uget
    sudo apt-get install aria2
    ```
2. pip
    ```sudo apt-get install python-pip```
    pip 速度慢：
    创建 /home/scuter/.pip/pip.conf 
    写入：
    ```
    [global]
    trusted-host =  mirrors.aliyun.com

    index-url = http://mirrors.aliyun.com/pypi/simple
    ```
3. 解决依赖问题
    ```
    sudo apt-get -f install
    ```
4. [apt用法](http://www.zhukun.net/archives/7577)
5. [美化](https://www.zivers.com/post/909.html)
    *注意 Ubuntu tweak在16.04已经不适用！！！用Unity Tweak tool替代*
6. Chrome
    ```
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
    sudo dpkg -i google-chrome-stable_current_amd64.deb
    ```
7. jupyter (使用python2和3的内核)
    ```
   python2 -m pip install ipykernel
    python2 -m ipykernel install --user

    python3 -m pip install ipykernel
    python3 -m ipykernel install --user
    ```
8. [mongodb](http://www.runoob.com/mongodb/mongodb-linux-install.html)

9. 显示系统状态：[System Load Indicator](https://apps.ubuntu.com/cat/applications/precise/indicator-multiload/)
10. 显示温度：[如何在 Ubuntu 中检查笔记本 CPU 的温度](https://linux.cn/article-5682-1.html)
11. [java](http://www.cnblogs.com/a2211009/p/4265225.html)
12. 图形化界面的vim
    ```
    sudo apt-get install vim-gtk
    ```



windows ubuntu 双系统共享蓝牙设备；
http://blog.csdn.net/captainarcher/article/details/41379885




# 问题记录
* 删除内核时 用uname -a先看看当前的内核 不要删了当前内核

* 挂起后wifi无法连接
    ```shell
    sudo service network-manager restart
    ```
    重启网卡若失效，只能重启电脑了

* 在中文输入法时数字,英文间隔变大,检查是否处于全角字符状态
* windows 和ubuntu 下时间不一致　　　
    Ubuntu中不使用UTC时间，而启用本地时间
    编辑
    */etc/default/rcS*
    把其中的内容“UTC=yes”改成“UTC=no“，保存后重启系统就可以了。
    或者
    ```
    sudo timedatectl set-local-rtc 1
    ```
* windows ubuntu 双系统[共享蓝牙设备](http://blog.csdn.net/captainarcher/article/details/41379885)

# 常用备忘

## 命令
* 删除软件
    ```
    sudo apt-get purge oracle-java8-installer
    ```
* ssh登陆远程例子：
    ```shell
    ssh root@192.168.199.1 -p 1022
    ```
* jobs 查看当前session创建的所有任务.包括 ctrl Z挂起任务 fg +对应的任务号 将任务调到前端 在用ctrl C停止任务.bg+任务号 让进程在后台继续运行。
* 可以通过文件系统自带的connect to server查看远程系统的文本
    多种协议：
    >sftp://address    
    >ftp://    
    >smb://

## 快捷键
Ctril+alt+t 在home启动终端
ctrl+H组合键使目录中的隐藏文件显示出来
