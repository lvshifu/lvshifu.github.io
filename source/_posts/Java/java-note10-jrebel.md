---
title: Java笔记10--好用的Tomcat免重启调试插件JRebel
date: 2017-06-07 16:24:03
tags: [Java,JRebel]
categories: 
---
# 好用的Tomcat免重启调试插件JRebel

JRebel是一个J2EE热部署的工具。使用它可以减少在项目的构建和部署上浪费的时间。比如在Eclipse上配合Tomcat开发时，class文件的变动会让WEB应用自动重启，而JRebel则可以动态监视class文件及配置文件，如果有文件更新，JRebel会重新加载class文件，达到热部署的目的。
<!--more-->
JRebel支持Eclipse、MyEclipse、IntelliJ、NetBeans等众多IDE。

个人开发者开发开源软件可以免费使用JRebel插件！登录 https://my.jrebel.com 这个网站，然后用Twitter或者Facebook账号登录这个网站，就能获得免费的激活码。

JRebel 7.0.10 亲测成功。
而且Eclipse里面注册完成后，其他IDE里面安装插件后无需再次注册。

    注意:JRebel 7.0 不需要手工配置了，会自动生成相应要监控的项目。从一个项目复制出另一个项目时，如果连其中的rebel.xml一起复制而忘记修改rebel.xml的内容时，会产生修改内容后不能及时反映的现象。一定要注意。

