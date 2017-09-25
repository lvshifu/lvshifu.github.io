---
title: Java笔记8--IDEA介绍
date: 2017-03-08 16:24:03
tags: [IDEA,Java]
categories: 
toc: false
---

最近Eclipse+Tomcat7调试经常停在Threadpoolexecutor，没找到好的解决办法，尝试换成IDEA。

IDEA是Jetbrains公司的产品，非常优秀的一个JAVA开发环境。
但是一些理念和Eclipse完全不同，从Eclipse转过来需要花费一定的时间来适应。
<!--more-->
开始阶段，可以参照下面的几篇文章。
http://club.oneapm.com/t/eclipse-intellij-idea/657
https://gist.github.com/xcaspar/fb83de83cbedc9cf09cb
http://www.ituring.com.cn/article/37792

http://www.infoq.com/cn/news/2013/11/why-drop-eclipse-use-intellij

熟悉后，IDEA的开发还是令人满意的，但要注意, IDEA开发WEB项目时默认是不热部署的，更新JAVA后，要重启Tomcat才能看到更新。不过可以在Tomcat设置的窗口里，设置

    On 'Update' action:    -> Restart server
    On frame deactivation: -> Update classes and resources，

这样更新JAVA后，再切换到浏览器时，tomcat自动更新classes和resources，达到热部署的效果。

附：
Q. Eclipse+Tomcat7调试经常停在java.util.concurrent.Threadpoolexecutor 1128行  

    processWorkerExit(w, completedAbruptly);

A. Eclipse+Tomcat7调试时经常碰到程序停在java.util.concurrent.Threadpoolexecutor，原因是Eclipse默认勾选了“Suspend execution on uncaught exceptions”，发生未捕获的异常时暂停执行。

解决方法： Window > Preferences > Java > Debug，取消勾选"Suspend execution on uncaught exceptions"

参考：https://stackoverflow.com/questions/6290470/eclipse-debugger-always-blocks-on-threadpoolexecutor-without-any-obvious-excepti

据说已经在Tomcat 7.0.54 and 8.0.6 中得到解决: https://issues.apache.org/bugzilla/show_bug.cgi?id=56492
