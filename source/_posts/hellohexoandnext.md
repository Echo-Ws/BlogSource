---
layout: 
title: Hello Hexo and Next!
date: 2018-05-09 21:39:04
tags: 
    - hexo 
    - next
categories: 杂记
---


{% note primary %} 
喜欢写Blog的人，会经历三个阶段:
第一阶段，刚接触Blog，觉得很新鲜，试着选择一个免费空间来写。
第二阶段，发现免费空间限制太多，就自己购买域名和空间，搭建独立博客。
第三阶段，觉得独立博客的管理太麻烦，最好在保留控制权的前提下，让别人来管，自己只负责写文章。
<p align="right">by 阮一峰</p>
{% endnote %}


  

<!--more-->
# 为什么要建站
1. 记录自己的学习过程
2. 面试的时候增加竞争力
3. 前端练手

大四以前一直被课业占满了，课本永远看不完，资料永远有下一篇。blog只能草草记录在csdn上。老实说，csdn等网上博客足够满足日常记录的需求。然而作为一个程序员，怎么能容忍一个不可以定制化的blog呢！一个完全属于自己的网站才是理想目标。
大二第一次了解到GitHub Page的时候，被jekyll和ruby劝退了。而如今Hexo+Next教程已经丰富只需要对着文档进行傻瓜式操作，技术门槛无限降低。
网上有很多Next的自定义教程，我就不重复造轮子了，在这里记录一下本站参考的教程。
* **注意很多教程由于时间的原因已被集成到Next本身，在配置前先在主题配置文件中搜对应的关键字往往能节省很多工作** *
1. [官方教程](http://theme-next.iissnan.com/getting-started.html)
2. [高度个性化配置](http://mashirosorata.vicp.io/HEXO-NEXT%E4%B8%BB%E9%A2%98%E4%B8%AA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE.html)
<del> [blog版本控制](https://formulahendry.github.io/2016/12/04/hexo-ci/)</del>
该文yml有误，没有升级node，造成hexo无法安装。在没找到下文前，想过通过脚本实现把blog更新且部署网页。
3. [使用AppVeyor持续集成你的Hexo博客](https://yangshunjie.com/Use-Appveyor-to-continuously-integrate-your-Hexo-blog.html)     !

---
作为一个blog，最重要的还是内容。
准备陆续整理一下[csdn博客](https://blog.csdn.net/solo_ws)里的博文搬运到此。
希望这篇能成为一个好的开端！
---
2018-9-18 update：

换新电脑后才发现当初没有把具体过程记录下来是很愚蠢的。
等于又要重新找一遍当初看过的资料。时间精力重复消耗。
最好记录下来做了些什么，迁移到新环境就轻松点。

对每一个hexo所在的文件夹都需要装hexo和server：
npm install hexo --save
npm install hexo-server --save

启动服务器：
hexo server

---
# 待做
- [ ]  [博客提交百度谷歌收录](https://blog.csdn.net/hosea1008/article/details/53384382) [seo](http://www.ehcoo.com/seo.html)
- [ ] 七牛图床
- [ ] 标签页变化js
- [ ] 建站日志
- [ ] 中英文版本切换
- [ ] 用数字显示阅读进度
- [ ] 文章之间的分割线
---
{% centerquote %}
引用方式备忘

**作者**
{% endcenterquote %}



---
2018-10-08

肉身翻墙后发现了很多做得很棒的blog，勾起了我美化站点的欲望。

大佬的blogs：
[reuixiy](https://reuixiy.github.io)
[diygod](https://diygod.me/)

在大佬网站中的友链又可以找到很多很棒的blogger。

希望了解静态网页可以实现的效果，首先需要了解什么是静态网页。
{% note primary %} 
静态网页不用访问数据库，本身就是一个完整可以显示的网页。
静态网页使用语言：HTML
动态网页使用语言：HTML+ASP或HTML+PHP或HTML+JSP等

静态网页的特点简要归纳如下：
（1）静态网页每个网页都有一个固定的URL，且网 页URL以.htm、.html、.shtml等常见形式为后缀，而不含“？”；
（2）网页内容一经发布到网站服务器上，无论是否有用户访问，每个静态网页都是保存在网站服务器上的，每个网页都是一个独立的文件；
（3）静态网页的内容相对稳定，因此容易被搜索引擎检索；
（4）静态网页没有数据库的支持，网站信息量很大时，完全依靠静态网页制作方式在网站制作和维护方面工作量较大，比较困难；
（5）静态网页的交互性较差，在功能方面有较大的限制 。
由于动态网页静态化的技术，一般网页前台的文件都是以htm、htm、shtml结尾。此类网站有后台，有数据库，前台页面与数据库没有任何交互的行为，此类网站与静态网站无异。可以视为静态网站。

当网页数量巨大时会造成较大的存储压力。
{% endnote %}

即可以修改next的模板来实现我任何需求。

