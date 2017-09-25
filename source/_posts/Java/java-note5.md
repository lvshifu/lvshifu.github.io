---
title: Java笔记5--Java开发常见错误集1
date: 2016-09-20 16:56:38
tags: [WEB开发,Java]
categories: 
list_number: false
---

## 1.Eclipse和MyEclipse的Workspace弄混
经常会有在文件管理器里直接操作文件的时候，在文件管理里操作了，但是在Eclipse里没有及时刷新同步，导致编译不及时，看不到改动后的效果。
还有的是按个人习惯，有多个Workspace，有时会在Eclipse里面操作WorkspaceA，而在文件管理器里操作WorkspaceB，进而产生怎么修改也不能生效的怪异现象。

<!--more-->

## 2.Eclipse和MyEclipse的Tomcat插件不同，对应的WEB APP目录也不同
通常Eclipse的插件生成的WEB APP目录位于Workspace的 .metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps， 而MyEclipse的插件对应的WEB APP目录位于Tomcat安装目录下。

Eclipse里面Tomcat启动时，只会启动Tomcat里面配置的应用，Tomcat安装目录下的应用不启动。
MyEclipse里面Tomcat启动时，Tomcat安装目录下的所有应用同时启动。

## 3.HTTP 404错误
* 分析Tomcat是否启动成功。
* Tomcat启动成功后，对应的应用是否启动成功。
* 应用启动成功后，对应的context path是否正确。
* 最后确认WEB应用的响应路径是否正确。

## 4.Jar包冲突
Tomcat自身有个lib目录，每个应用自身在WEB-INF目录下也都有个lib目录，通常Tomcat的lib目录里面存放的是所有WEB APP共通的jar包，另外Jdk自身还有个lib目录。
使用全新的Jdk、Tomcat进行开发，通常不会发生问题。但是如果利用老的Jdk、Tomcat进行开发，或者对老项目进行功能追加时就要注意了，新增加的Jar包放到WEB-INF下的lib后，有时会发生莫名其妙的不生效的问题，甚至还会出错，这时一盘要考虑一下是不是发生Jar包冲突了。检查Tomcat的lib目录，然后检查Jdk的lib目录。确认是否有问题。

通常使用一些文件转换工具包或者短信猫之类的工具会往Tomcat的lib目录或者Jdk的lib目录下放入Jar包。在这种情况下尤其要注意。

## 5.JDK高版本在Tomcat低版本上不能识别
使用JDK8等编译的class文件在低版本Tomcat上不能识别。

## 6.清楚自己的代码在WEB应用中执行的顺序
对于通常的SSH架构来说，从浏览器里输入一个地址，到最后展现页面，会有下面的步骤：
1. Tomcat接收URL，分析由哪个应用来相应（定位到开发中的应用）。
2. 应用中的Struts分析URL，分配适配的Action和方法处理URL请求。
3. Action取得URL中的参数，或者POST的参数。
4. 执行Action中适配的方法（自己的业务逻辑、调用Service、DAO等）。
5. 通过return语句和Struts配置，确定要展现的JSP（JSON的时候，返回封装的JSON）。
6. 编译JSP到Servlet，标签转换（Struts标签和自定义标签）。
7. 执行编译好的Servlet，输出html格式的内容。
8. IE拿到HTML内容，分析内容，并读取关联JS和CSS。
9. 加载DOM过程中顺序执行JS。
10. 执行加载DOM完成后的JS（documnet.ready）。
11. 执行onload。

## 7.上线后外网404
1. ping域名，看域名解析是否出错.
2. 内网中确认是否404.
3. 外网404页面分析，看是否有特殊标志，如WAF等，可能是防火墙等的原因。
4. 查看网络拓扑，分析是否是由于端口转发、映射，或者反向代理出错等。


