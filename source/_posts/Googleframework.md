---
layout: 
title:  Install official ROM and Google Playstore
date: 2018-09-04 8:39:04
tags: 
    - Android
    

categories: 杂记
---
# 刷谷歌框架
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

# 使用中遇到的问题
   1. root
   完成上述步骤后手贱想root，结果再次登入Google play 需要重新验证账号，点击无反应。尝试设置 账户 中删除Google账号 提示管理员禁止删除该账号 放弃。只能再次恢复出厂设置。

   也试过先root后再登入Google账号，Google play 闪退。装上re文件浏览器 检查webviewgoogle的确还原了 无解。

   2. 验证身份 
   使用一段时间后出现“需要验证身份，您需要登陆自己的google账号”。 使用电脑登陆自己的Google账号，在最近的设备中将权限删除，等待手机的Googleplay提示重新输入密码验证账号即可。
   还可以再出现该提示信息的时候断网，恢复联网后提示消失。

   3. 无法下载软件
   无法在谷歌商店中更新或是下载任何软件。重启后第一次打开谷歌商店可以下载，之后则不行。试过清除缓存或重登账号无解。

   4. 谷歌框架自带的电话app再查看童话记录时闪退。
   无解。考虑换一个app查看通话记录。

   考虑换官方国际ROM，客服的说法是Z17没有在国际发售故没有出国际版的ROM 
   