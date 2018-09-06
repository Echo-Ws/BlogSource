---
layout: 
title:  Install official ROM and Google Playstore
date: 2018-09-04 8:39:04
tags: 
    - Android
    

categories: 杂记
---

参考:
[努比亚z17安装谷歌框架](https://zhuanlan.zhihu.com/p/37108883)

1. 刷入第三方Recovery: TWRP
   绯色玻璃最新版的工具包里没有root，故网上找 时代的导航者 做的twrp。
    进入设置-关于手机-版本号，对着版本号这里连点5下，进入开发者模式并打开USB调试。
    打开对应的bat文件完成twrp安装。
    此时在BootLoader界面，手动按音量下选择Reboot to recovery mode进入recovery。
    在工具箱找到root，root完重启。
2. 刷机，与参考类似
   安装re文件管理器，备份/system/app目录下的WebViewGoogle。
   到 [Open Gapps ]( https://opengapps.org/)选择arm64，Android 7.1。后一个包看需求选。但笔者在选pico包 后出现 安装任何app都显示“此应用与您的所有设备都不兼容 ”。故最后选择的是micro。
   将下载好的压缩包放入手机。关机 摁住上音量键/ 通过bat 进入recover模式 选择安装，找到方才保存的包即可。
   安装完ROM后重启。通过re文件浏览器将WebViewGoogle复原。

   进入设置-高级设置-恢复出厂设置后即可使用Google play。

   完成上述步骤后手贱想root，结果再次登入Google play 需要重新验证账号，点击无反应。尝试设置 账户 中删除Google账号 提示管理员禁止删除该账号 放弃。只能再次恢复出厂设置。

   也试过先root后再登入Google账号，Google play 闪退。装上re文件浏览器 检查webviewgoogle的确还原了 无解。

