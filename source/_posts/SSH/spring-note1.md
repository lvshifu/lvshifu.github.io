---
title: Spring笔记1-Spring介绍
date: 2017-07-17 21:18:02
tags: [Spring]
categories:
---

# Spring是什么
<!--more-->

Spring徹底入門 Spring FrameworkによるJavaアプリケーション開発

    『Expert One-on-One:J2EF, Design and Development』の刊行から約1年後、2004年には、EJB (Enterprise
    JavaBeans)を使わずにSpring Framework1.0を用いて、堅牢なJ2EEアブリケーションを開発する方法を解説した Juergen Hoeller 氏との共著『Expert One-on-One: J2EE Development without EJB』が刊行されました。さらに1年後の2005年にはSpring Framework 1.2の機能をカバーした書籍『Professional Java Development with
    the Spring Framework』が刊行されています。

    Spring Frameworkl.x では、IoC (Inversion of Control)コンテナ（本書では「DIコンテナ」と呼びます)、AOP (Aspect Oriented Programming)、XMLベースのBean定義、フレームワークモジュール間の疎結合化、トランザクション管理、データアクセスなどを基本的なフレームワークの機能として実現しています。この頃は、Spring FrameworkをStruts、Hibernateと組み合わせて使うSSH(Struts、Spring Framework、Hibernate)が最先端のフレームワーク構成となっていました。

    2006年に、Spring Framework 2.0 がリリースされ、Spring Security や Spring Web Flow など、Web アブリケーション開発に必要なものを中心にSpring Frameworkの周辺プロジェクトがいくつか立ち上がりました。2007年には、アノテーションベースの DI (Dependency Injection}や MVC (Model View Controller〉に対応したSpring Framework 2.5がリリースされ、システム間連携やバッチ処现を実現するSpring IntegrationやSpring Batchといった周辺プロジェクトが立ち上がりました。また、Spring Frameworkは、Rod Johnson氏が起業した「Interface21」で開発されていましたが、「SpringSource」と名称を変更し、拠点をそれまでのヨーロッパから米国へと移しました、米国に拠点を移してからSpringSourceはベンチャーキャビタルからの投資を受け、TomcatやApacheのサポートを手掛けるCovalent、GroovyやGrailsを開発するG2One、監視ソリューションを提供するHypericといった企業を次々と買収しました。Javaのアプリケーションフレームワークの提供だけでなく、アプリケーションサーバーなどのシステム基盤、システム全体の監視など、エンターブライズ開発におけるソフトウェアのトータルソリューション提供を狙っていることが伺えます。また、この頃からSpring Tool Suiteと呼ばれるSpring Frameworkの統合開発琛境の提供が始まりました。

    2009年に、Spring Framework 3.0がリリースされ、JavaベースコンフィギュレーションやDIのJava仕様である JSR 330 に対応しました。また、JPA (Java Persistence API) 2.0 や Bean Validation など、Java Platform,Enterprise Edition (Java EE〉6の仕様についても早い段階でサポートしました。Spring Framework 3.0からRESTfulなフレームワークとして利用できるようにSpring MVCを大きく改善しています。

    2009年には、SpringSourceがVMwareに買収されるという当時のJava開発者には衝撃的な事件がありました。同じ年にはOracleによるSun Microsystems 買収もあり、Java業界はどのような方向へ進むのかと、IT業界全体が大きく摇れた年でもありました。 VMwareおよびEMCとともに、ハードからソフトまでの垂直統合の重要なピースになると見られていましたが、Cloud Foundryとの連携といった一部の連携以外は、ほぼ従来のSpringSourceの文化を引き継ぎ、従來どおりの開発スタイルが引き継がれました。

    2013年に、Spring Framework 4.0がリリースされ、Java SE 8 や Java EE 7への対応、WebSocket や Web メッセージングのサポートなどを実施しています。この年、VMwareが買収したいくつかのソフトウェアブロダクトと一緒にSpring FrameworkはPivotalという新しい会社にスピンオフしています。スビンオフすることで、よりオーブンソース活動を活性化し、スタートアップの企業文化で開発し、普及展開することを狙っています。2014年には、昨今注目されているSpring BootやSpringIO Platformプロジェクトが始まりました。


What's new in Spring 2.0?

    2.1. Introduction
    2.2. The Inversion of Control (IoC) container
    2.2.1. Easier XML configuration  ★★★
    2.2.2. New bean scopes
    2.2.3. Extensible XML authoring
    2.3. Aspect Oriented Programming (AOP)
    2.3.1. Easier AOP XML configuration
    2.3.2. Support for @AspectJ aspects  
    2.4. The Middle Tier
    2.4.1. Easier configuration of declarative transactions in XML
    2.4.2. JPA
    2.4.3. Asynchronous JMS
    2.4.4. JDBC
    2.5. The Web Tier
    2.5.1. A form tag library for Spring MVC
    2.5.2. Sensible defaulting in Spring MVC
    2.5.3. Portlet framework
    2.6. Everything else
    2.6.1. Dynamic language support
    2.6.2. JMX
    2.6.3. Task scheduling
    2.6.4. Java 5 (Tiger) support

What's new in Spring 2.0 and 2.5?

    2.1. Introduction
    2.2. The Inversion of Control (IoC) container
    2.2.1. New bean scopes
    2.2.2. Easier XML configuration
    2.2.3. Extensible XML authoring
    2.2.4. Annotation-driven configuration  ★★★
    2.2.5. Autodetecting components in the classpath  ★★★
    2.3. Aspect Oriented Programming (AOP)
    2.3.1. Easier AOP XML configuration
    2.3.2. Support for @AspectJ aspects
    2.3.3. Support for bean name pointcut element  ★★★
    2.3.4. Support for AspectJ load-time weaving  ★★★
    2.4. The Middle Tier
    2.4.1. Easier configuration of declarative transactions in XML  ★★★
    2.4.2. Full WebSphere transaction management support
    2.4.3. JPA
    2.4.4. Asynchronous JMS
    2.4.5. JDBC
    2.5. The Web Tier
    2.5.1. Sensible defaulting in Spring MVC
    2.5.2. Portlet framework
    2.5.3. Annotation-based controllers  ★★★
    2.5.4. A form tag library for Spring MVC
    2.5.5. Tiles 2 support
    2.5.6. JSF 1.2 support
    2.5.7. JAX-WS support
    2.6. Everything else
    2.6.1. Dynamic language support
    2.6.2. Enhanced testing support
    2.6.3. JMX support
    2.6.4. Deploying a Spring application context as JCA adapter
    2.6.5. Task scheduling
    2.6.6. Java 5 (Tiger) support

What’s New in Spring Framework 3.x

    New Features and Enhancements in Spring Framework 3.1
    3.1. Cache Abstraction
    3.2. Bean Definition Profiles  ★★★
    3.3. Environment Abstraction
    3.4. PropertySource Abstraction
    3.5. Code equivalents for Spring's XML namespaces  ★★★
    3.6. Support for Hibernate 4.x
    3.7. TestContext framework support for @Configuration classes and bean definition profiles  ★★★
    3.8. c: namespace for more concise constructor injection
    3.9. Support for injection against non-standard JavaBeans setters
    3.10. Support for Servlet 3 code-based configuration of Servlet Container  ★★★
    3.11. Support for Servlet 3 MultipartResolver
    3.12. JPA EntityManagerFactory bootstrapping without persistence.xml
    3.13. New HandlerMethod-based Support Classes For Annotated Controller Processing
    3.14. "consumes" and "produces" conditions in @RequestMapping
    3.15. Flash Attributes and RedirectAttributes
    3.16. URI Template Variable Enhancements
    3.17. @Valid On @RequestBody Controller Method Arguments
    3.18. @RequestPart Annotation On Controller Method Arguments
    3.19. UriComponentsBuilder and UriComponents

    New Features and Enhancements in Spring Framework 3.2
    4.1. Support for Servlet 3 based asynchronous request processing
    4.2. Spring MVC Test framework
    4.3. Content negotiation improvements
    4.4. @ControllerAdvice annotation
    4.5. Matrix variables
    4.6. Abstract base class for code-based Servlet 3+ container initialization
    4.7. ResponseEntityExceptionHandler class
    4.8. Support for generic types in the RestTemplate and in @RequestBody arguments
    4.9. Jackson JSON 2 and related improvements
    4.10. Tiles 3
    4.11. @RequestBody improvements
    4.12. HTTP PATCH method
    4.13. Excluded patterns in mapped interceptors
    4.14. Using meta-annotations for injection points and for bean definition methods  ★★★
    4.15. Initial support for JCache 0.5
    4.16. Support for @DateTimeFormat without Joda Time
    4.17. Global date & time formatting
    4.18. New Testing Features
    4.19. Concurrency refinements across the framework
    4.20. New Gradle-based build and move to GitHub  ★★★
    4.21. Refined Java SE 7 / OpenJDK 7 support


What’s New in Spring Framework 4.x

    3. New Features and Enhancements in Spring Framework 4.0
    3.1. Improved Getting Started Experience
    3.2. Removed Deprecated Packages and Methods
    3.3. Java 8 (as well as 6 and 7)
    3.4. Java EE 6 and 7
    3.5. Groovy Bean Definition DSL
    3.6. Core Container Improvements
    3.7. General Web Improvements
    3.8. WebSocket, SockJS, and STOMP Messaging
    3.9. Testing Improvements
    4. New Features and Enhancements in Spring Framework 4.1
    4.1. JMS Improvements
    4.2. Caching Improvements
    4.3. Web Improvements
    4.4. WebSocket Messaging Improvements
    4.5. Testing Improvements
    5. New Features and Enhancements in Spring Framework 4.2
    5.1. Core Container Improvements
    5.2. Data Access Improvements
    5.3. JMS Improvements
    5.4. Web Improvements
    5.5. WebSocket Messaging Improvements
    5.6. Testing Improvements
    6. New Features and Enhancements in Spring Framework 4.3
    6.1. Core Container Improvements
    6.2. Data Access Improvements
    6.3. Caching Improvements
    6.4. JMS Improvements
    6.5. Web Improvements
    6.6. WebSocket Messaging Improvements
    6.7. Testing Improvements
    6.8. Support for new library and server generations

Spring核心功能：

IoC(Inversion of Control)控制反转
DI(Dependency Injection)依赖注入
AOP(aspect-oriented programming)面向切面编程

Spring 1.x 通过XML配置文件实现解耦
Spring 2.0 初步引入注解配置
Spring 2.5 @Autowired, 增加了component-scan, 大大减少了配置工作量
Spring 3.x 开始支持JavaConfig

Spring3.0以后不再提供一个大的完整的jar包，而是分成多个小的jar包
