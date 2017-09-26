---
title: Java笔记11--WEB开发发展历程梳理
date: 2017-09-08 16:24:03
tags: [WEB开发,Java]
categories:
---


# HTML与WWW
<!--more-->
百度百科关于HTML的介绍

    网页的本质就是超级文本标记语言，通过结合使用其他的Web技术（如：脚本语言、公共网关接口、组件等），可以创造出功能强大的网页。因而，超级文本标记语言是万维网（Web）编程的基础，也就是说万维网是建立在超文本基础之上的。超级文本标记语言之所以称为超文本标记语言，是因为文本中包含了所谓“超级链接”点。

    超文本标记语言（第一版）——在1993年6月作为互联网工程工作小组（IETF）工作草案发布（并非标准）：
    HTML 2.0——1995年11月作为RFC 1866发布，在RFC 2854于2000年6月发布之后被宣布已经过时
    HTML 3.2——1997年1月14日，W3C推荐标准
    HTML 4.0——1997年12月18日，W3C推荐标准
    HTML 4.01（微小改进）——1999年12月24日，W3C推荐标准
    HTML 5——2014年10月28日，W3C推荐标准

百度百科关于WWW的介绍

    1989年3月，伯纳斯－李撰写了《关于信息化管理的建议》一文，文中提及ENQUIRE 并且描述了一个更加精巧的管理模型。1990年11月12日他和罗伯特·卡里奥（Robert Cailliau）合作提出了一个更加正式的关于万维网的建议。在1990年11月13日他在一台NeXT工作站上写了第一个网页以实现他文中的想法。
    在那年的圣诞假期，伯纳斯·李制作了要一个网络工作所必须的所有工具[6]：第一个万维网浏览器（同时也是编辑器）和第一个网页服务器。
    1991年8月6日，他在alt.hypertext新闻组上贴了万维网项目简介的文章。这一天也标志着因特网上万维网公共服务的首次亮相。
    1994年10月在拥有“世界理工大学之最”称号的麻省理工学院（MIT）计算机科学实验室成立万维网联盟，又称W3C理事会。。建立者是万维网的发明者蒂姆·伯纳斯·李。蒂姆·贝尔纳斯·李是万维网联盟（W3C）的领导人，是Web技术领域最具权威和影响力的国际中立性技术标准机构。

# 静态网页阶段


```sequence
浏览器->WEB服务器: 你好，我要查看/aaa/bbb.html.
Note right of WEB服务器: 在服务器主目录下查找/aaa/bbb.html.
WEB服务器->浏览器: 返回/aaa/bbb.html!
```

动态内容基本上为GIF。

# CGI动态网页阶段

```sequence
浏览器->WEB服务器: 你好，我要查看/news/id=123.
WEB服务器-->CGI: 转发请求.
CGI-->外部程序: 要求生成id为123的news页面.
Note right of 外部程序: 生成id为123的news页面.
外部程序-->CGI: 返回id为123的news页面.
CGI-->WEB服务器: 转发结果.
WEB服务器->浏览器: 返回id为123的news页面.
```

[CGI](https://en.wikipedia.org/wiki/Common_Gateway_Interface)标准订立于1993年。
CGI(Common Gateway Interface) 是WWW技术中最重要的技术之一，有着不可替代的重要地位。CGI是外部应用程序（CGI程序）与WEB服务器之间的接口标准，是在CGI程序和Web服务器之间传递信息的过程。
CGI可以用任何一种语言编写，只要这种语言具有标准输入、输出和环境变量。比如Perl、Shell、C、C++等。
要让CGI程序在服务器上正常运行，必须按照使用的服务器类型以及它的设置要求把CGI程序放在某一特定的目录中或使其带有特定的扩展名。

[FastCGI](https://en.wikipedia.org/wiki/FastCGI)是CGI的一个变体，初始目的是为了解决CGI程序引起的服务器过载。

# PHP/ASP/JSP动态脚本阶段

```sequence
浏览器->WEB服务器: 我要查看2012年的销售报表（/salesreport/id=2012）.
WEB服务器-->Servlet容器: 转发请求.
Servlet容器-->数据库:
Note right of Servlet容器: 生成2012年的销售报表页面.
数据库-->Servlet容器:
Servlet容器-->WEB服务器: 返回2012年的销售报表页面.
WEB服务器->浏览器: 返回2012年的销售报表页面.
```

动态脚本优于CGI技术的在于简单易用和高性能。

PHP诞生于1994年。
ASP 1.0 规范制定于1996年。
Servlet 1.0规范制定于1997年。
1999年J2EE诞生。
2000年.net平台诞生。

# MVC框架阶段

随着大型网站的开发，代码越来越复杂，辅助WEB开发的技术框架层出不穷。

2000年诞生了非常流行的Struts框架。MVC模式得到广泛的应用。
2008年12月，Struts1发布了最后一个正式版（1.3.10）。
2013年4月5日，Struts开发组宣布终止了Struts 1的软件开发周期。

2005年12月，WebWork宣布WebWork 2.2以Apache Struts 2的名义合并至Struts。
2007年2月第一个全发布（full release）版本释出。

Spring 第一版由 Rod Johnson 开发，并在2002年10月发布在 Expert One-on-One J2EE Design and Development 一书中。2003年6月，Spring Framework 第一次发布在 Apache 2.0 许可证下。2004年3月，发布了里程碑的版本1.0.

```sequence
WEB服务器->Servlet容器: 转发请求.
Servlet容器-->Action Servlet:
Note right of Action Servlet: Action,Form,config.xml(Controller)
Action Servlet-->Model Beans:
Model Beans-->Database:
Note right of Model Beans: ORM(Model)
Database-->Model Beans:
Model Beans-->Action Servlet:
Action Servlet-->Servlet容器: 返回JSP(View)
Servlet容器->WEB服务器: 返回结果.
```

ORM框架
iBATIS，2001年，2010/06/16，改名mybatis。
Hibernate，2001年。


# AJAX技术发展

1995年,NetScape公司设计了JavaScript，在浏览器上运行脚本语言为网页增加动态性。
AJAX（Asynchronous JavaScript and XML）基于JavaScript的XmlHttpRequest，用于创建交互性更强​的Web应用。
随着Google在自家产品中的应用而迅速得到推广。

AJAX之前，浏览器向服务器发送请求，服务器返回一个响应页面，然而连续的多个请求返回的页面中，可能大部分内容是一样的，这样就产生了很大的流量和带宽的浪费。而AJAX请求从服务器得到的数据仅包含要变动的部分，通过JavaScript把变动的部分更新到页面上，大大减少了浏览器和服务器之间交互的内容。

# MVC前端框架阶段

Backbone, Angular, Knockout, Ionic


# 未来
1. CGI并不是一个多么不好的技术，在FastCGI、SimpleCGI等基础上，有一些非常好的实现，也可以达到高性能、高并发的需求。在Python、PHP的世界多有应用。
1. WEB服务器和Servlet容器以及应用服务器要区分开来，通常开发过程中只用Tomcat，这时Tomcat实际上担当了读个角色。
