---
title: SSH笔记1-SSH介绍
date: 2017-07-28 15:18:02
tags: [SSH]
categories:
---

# SSH是什么

SSH框架一般指的是Struts、Spring、Hibernate，后来Struts2代替了Struts。

SSM框架一般指的是Spring MVC、Spring、MyBatis。

<!--more-->

# 标准SSH框架

## Struts
Struts1(2000年~2008年12月)，最后一个正式版（1.3.10）。
2013年4月5日，Struts开发组宣布终止了Struts 1的软件开发周期。

Struts2(2007年2月~)
Struts2并不是Struts1的升级版，而是由WebWork 2.2变化而来。

## Spring
* 2002年10月 Rod Johnson 主要针对J2EE的繁琐问题发表了《Expert One-on-One J2EE Designand Development》，本书包含3万行代码。这些代码被称为Interface 21 Framework；Juergen Hoeller和Yann Caroff联系Rod Johnson 将代码开源，并由Yann Caroff提出Spring这个词。
* 2003年6月 Spring 0.9在Apache 2.0协议下发布，Juergen和Yann成为Interface 21的创始人，Interface 21也支持AspectJ Project，Thomas Risberg负责Spring JDBC，Ben Alex将Acegi Security的代码送给Rod和Juergen。
* 2004年3月 Spring Framework 1.0问世。
* 2005年 Spring Framework达40万下载量。
* 2006年8月 Spring 2.0发布，Spring超过100万次下载。
* 2007年9月 Spring 2.5发布。
* 2008年 Interface 21改名为Spring Source，Spring超过300万次下载。
* 2008年 SpringSource买下G2One公司（Groovy and Grails）。
* 2009年8月 VMWare 收购了SpringSource。
* 2009年12月 Spring 3.0发布。
* 2013年4月 VMware与EMC及通用电气建立了合资公司GoPivotal，Spring移到了Pivotal。年底Spring 4.0发布。
* 2014年9月 Spring4.1发布。
* 2015年7月 Spring4.2发布。
* 2016年6月 Spring4.3发布。

JDK 8+ for Spring Framework 5.x(SNAPSHOT)
JDK 6+ for Spring Framework 4.x
JDK 5+ for Spring Framework 3.x
JDK 1.4+ for Spring Framework 2.5
JDK 1.3+ for Spring Framework 2.0

[What's New in the Spring Framework](https://github.com/spring-projects/spring-framework/wiki/What%27s-New-in-the-Spring-Framework)

[Spring 各版本下载](http://repo.spring.io/release/org/springframework/spring/)

下面的Spring docs可以查看Spring所有版本的RELEASE NOTE。
[Spring docs](https://docs.spring.io/spring/docs/)

Spring核心功能：

IoC(Inversion of Control)控制反转
DI(Dependency Injection)依赖注入
AOP(aspect-oriented programming)面向切面编程

Spring 1.x 通过XML配置文件实现解耦
Spring 2.0 初步引入注解配置
Spring 2.5 @Autowired, 增加了component-scan, 大大减少了配置工作量
Spring 3.x 开始支持JavaConfig

Spring3.0以后不再提供一个大的完整的jar包，而是分成多个小的jar包

## Hibernate

    2001年，澳大利亚墨尔本一位名为Gavin King的27岁的程序员，上街买了一本SQL编程的书，他厌倦了实体bean，认为自己可以开发出一个符合对象关系映射理论，并且真正好用的Java持久化层框架，因此他需要先学习一下SQL。这一年的11月，Hibernate的第一个版本发布了。
    2002年，已经有人开始关注和使用Hibernate了。
    2003年9月，Hibernate开发团队进入JBoss公司，开始全职开发Hibernate，从这个时候开始Hibernate得到了突飞猛进的普及和发展。
    2004年，整个Java社区开始从实体bean向Hibernate转移，特别是在Rod Johnson的著作《Expert One-on-One J2EE Development without EJB》出版后，由于这本书以扎实的理论、充分的论据和详实的论述否定了EJB，提出了轻量级敏捷开发理念之后，以Hibernate和Spring为代表的轻量级开源框架开始成为Java世界的主流和事实标准。在2004年Sun领导的J2EE5.0标准制定当中的持久化框架标准正式以Hibernate为蓝本。
    2006年，J2EE5.0标准正式发布以后，持久化框架标准Java Persistent API（简称JPA）基本上是参考Hibernate实现的，而Hibernate在3.2版本开始，已经完全兼容JPA标准。

2015年08月 v5.0.0Final
2011年12月 v4.0.0Final
2005年03月 v3.0.0Final
2003年06月 v2.0.0Final
2002年07月 v1.0.0Final

## SSH深入理解

[深入浅出的理解框架（Struts2、Hibernate、Spring）与 MVC 设计模式](http://www.cnblogs.com/itao/archive/2011/08/22/2148844.html)
[Spring发展历程总结](http://www.cnblogs.com/RunForLove/p/4641672.html)


## 公司框架发展
+ 2007 JDK1.4+Struts1.x+Hibernate2.x
+ 2008 JDK1.4+Struts1.x+Spring2.x+Hibernate2.x
+ 2010 JDK1.5+Struts2.x+Spring3.x+Hibernate3.3x
+ 2012 JDK1.5+Struts2.1+Spring3.0+Hibernate3.3
+ 2013 JDK1.7+Struts2.3.15.1（REST）+Spring3.2.2+Hibernate4.2+JPA2.0+Spring Security 3.1.3+Spring Data1.4.0+Jackson2.1.4+Sitemesh2.4.2
+ 2016 JDK 1.7 + Spring MVC 4.1 + Spring 4.1 + Mybatis 3.3	+ Apache Shiro 1.2 + Servlet 3.0 + Jackson2.5 + Sitemesh2.4


# 海事框架
struts2-core-2.3.16.1.jar
spring.jar v2.5.2
hibernate3.jar v3.2.6.ga
easyui

# 2013框架
struts2-core-2.3.15.1.jar
spring-core-3.2.4.RELEASE.jar
hibernate-core-4.2.0.Final.jar
hibernate-jpa-2.0-api-1.0.1.Final.jar
spring-security-core-3.1.3.RELEASE.jar
sitemesh-2.4.2.jar
CUI

# 海事框架 和 2013框架比较


## 配置（struts.xml）


### 海事框架

    <struts>
      <constant name="struts.enable.DynamicMethodInvocation"
        value="false" />
      <constant name="struts.mapper.class"    
            value="ces.jcpt.core.struts.UserDefinedActionMapper" />
      <constant name="struts.i18n.encoding" value="UTF-8"></constant>
      <constant name="struts.devMode" value="false" />
      <constant name="struts.multipart.saveDir" value="/upload"/>
      <constant name="struts.multipart.maxSize" value="1073741824"/>
      <package name="jcpt-global" namespace="/jcpt"
        extends="struts-default">
        <global-results>
          <result name="error">/common/Error.jsp</result>
          <result name="success">/common/Success.jsp</result>
          <result name="json">/common/JsonData.jsp</result>
          <result name="jsonFoAjax">/common/JsonData2.jsp</result>
          <result name="forward">${forward}</result>
        </global-results>
      </package>

      <package name="jcpt" namespace="/jcpt" extends="jcpt-global">
        <action name="*@*" method="{1}" class="ces.jcpt.business.action.{2}">
          <result name="input">/common/Error.jsp</result>
        </action>
      </package>
    </struts>

```java
package ces.jcpt.business.action;

public class AnswerAction {
    public String addOrUpdate() {
        String forward = "/jcpt/website/zxsl/zxdb/answer.jsp";
        setForward(forward);
        return "forward";
    }
}
```

对于上面的AnswerAction来说，对应的配置为

```
      <package name="jcpt" namespace="/jcpt" extends="jcpt-global">
        <action name="addOrUpdate@AnswerAction" method="addOrUpdate" class="ces.jcpt.business.action.AnswerAction">
          <result name="input">/common/Error.jsp</result>
        </action>
      </package>
```

即访问URL为 <code>/jcpt/addOrUpdate@AnswerAction</code>。

但是在<code>UserDefinedActionMapper</code>中，覆盖了<code>DefaultActionMapper</code>，所以<code>/jcpt/admin/xxxxx/addOrUpdate@AnswerAction</code> 这样的URL也可以正常处理。

### 2013采用免配置方案

struts2-convention-plugin-2.3.15.1.jar
convention-plugin采用"约定大于配置”的思想，实现零配置。

https://struts.apache.org/docs/convention-plugin.html
http://javeye.iteye.com/blog/358744
http://www.blogjava.net/fancydeepin/archive/2012/10/26/struts2_convention_plugin.html

struts2-config-browser-plugin-2.3.15.1.jar
config-browser-plugin用于在运行时浏览项目中的载入Struts配置，包括所有action及其与jsp view的映射。
如果不清楚Action最终出来的url是啥，或者不清楚某个url最终会对应到哪个jsp文件，访问下面的URL即可。
http://localhost:8080/{你的项目名称}/config-browser/
http://localhost:8080/{你的项目名称}/config-browser/actionNames.xhtml

convention-plugin使用后，所有Action不再继承自默认defaultStack对应的package

struts2-rest-plugin-2.3.15.1.jar
rest-plugin用于让struts2支持REST风格。
https://www.ibm.com/developerworks/cn/java/j-lo-struts2rest/

```
    <struts>
      <!--constant name="struts.devMode" value="true" /-->
      <constant name="struts.mapper.alwaysSelectFullNamespace" value="false" />
        <!-- 取消Rest只有在出错或Get方式才返回数据限制 -->
      <constant name="struts.rest.content.restrictToGET" value="false"/>

      <constant name="struts.i18n.encoding" value="UTF-8"/>
        <!-- Action的类名以Controller为后缀 -->
        <constant name="struts.convention.action.suffix" value="Controller"/>
      <!-- Action中没有@Action注解也创建映射 -->
        <constant name="struts.convention.action.mapAllMatches" value="true"/>
        <constant name="struts.convention.result.flatLayout" value="false"/>
        <!-- Action默认REST风格，继承rest-default -->
        <constant name="struts.convention.default.parent.package" value="rest-default"/>

      <!-- Action类所在的包 -->
      <!--constant name="struts.convention.action.packages" value="com.ces.xarch.core.web"/-->
      <!-- 设置Convention插件文件协议类型 -->
        <constant name="struts.convention.action.fileProtocols" value="jar,zip,wsjar" />
      <!-- 设置Convention插件需要搜索的jar包 -->
        <constant name="struts.convention.action.includeJars" value=".*?/xarch-\d+\.\d+\.\d+\.jar(!/)?,.*?/xarch-security-\d+\.\d+\.jar(!/)?,.*?/*-plugin-\d+\.\d+\.jar(!/)?,.*/xarch-project-*?jar(!/)?" />
      <!-- 搜索以web为结尾的包 -->
        <constant name="struts.convention.package.locators" value="action,actions,struts,struts2,web"/>
      <!-- 不扫描的包 -->
      <constant name="struts.convention.exclude.packages" value="com.ces.xarch.core.web" />
        <!-- 页面文件存放位置 -->
      <constant name="struts.convention.result.path" value="/WEB-INF/views"/>
      <!-- 设置不需要处理的资源，多个用“,”进行分隔 -->
      <constant name="struts.action.excludePattern" value="/services/.*,/res/.*,/views/.*"/>

      <!-- 指定允许上传的文件最大字节数。默认值是2097152(2M)，现修改为1G -->
        <!--constant name="struts.multipart.maxSize" value="1073741824"/-->
        <!-- 设置上传文件的临时文件夹,默认使用javax.servlet.context.tempdir -->
        <!--constant name="struts.multipart.saveDir " value="d:/tmp" /-->

      <!-- 注意，在最新的struts2版本中，要想在JSP中通过OGNL表达式访问静态方法，则必须配置如下constant： -->
      <!--constant name="struts.ognl.allowStaticMethodAccess" value="true"/-->
    </struts>
```

从上面的配置看，应用自动搜索以 <code>action,actions,struts,struts2,web</code> 结尾的包，查找以Controller结尾的类。
Convention默认去掉类名的后缀（此处为Controller）部分。然后将将每个分部的首字母转为小写，用’-’分割，来确定URL。
如：CaseInfoController.java -> case-info, TaskController -> task 。

```java
@Namespaces({
	@Namespace("/voiture")
})
public class VoitureDispatchManageController{
  	public Object applyIndex() {
	    	return new DefaultHttpHeaders("applyIndex").disableCaching();
	  }
}
```
上面的applyIndex对应的URL即为 /voiture/voiture-dispatch-manage!applyIndex
映射路径为 /WEB-INF/views/voiture/voiture-dispatch-manage/applyIndex.*

    task!index         没有后缀：返回JSPX、VM、JSPF、JSP、FTL、HTML、HTM文件
    task!index.json    json：返回json字符串
    task!index.xml     xml：返回xml字符串


## 默认路由

|HTTP方法| URI	             |调用Action方法	| 请求参数  	| 返回资源	          | 说明 |
|--------|-------------------|--------------|--------------|-------------------|---------|
|GET     |/test	             | index		    |              |test/index.*
|GET     |/test/2	           | show       	|id=2	         |test/index-show.*	  |属性过滤|
|GET     |/test/2/edit       | edit       	|id=2	         |test/index-edit.*	  |属性过滤|
|GET     |/test/new	         | editNew		  |              |test/index-new.*	  |
|POST    |/test	             | create	      |           	 |success.jsp	        |
|PUT     |/test/2	           | update	       |id=2	       |success.jsp	        |
|DELETE	 |/test/2	           | destroy	     |id=2	        |success.jsp	      |
|POST	   |/test!search       | search	       |             	|test/index-list.*	|属性过滤,数据模型,	查询参数|
|POST	   |/test!coflow	     | coflow		      |             |test/index-coflow.*|	属性过滤,工作流参数|
|POST	   |/test!coflowList	 | coflowList		  |             |test/index-coflow-list.*	|属性过滤,工作流参数,	数据模型,	查询参数|
|POST	   |/test!coflowCount	 | coflowCount		|             |                    	|工作流参数|



## 分层

### 海事框架
Action  <-->  Bo  <--> HibernateDao  <--> Bean

DAO层缩减为HibernateDao，Bo层通过Hibernate的DetachedCriteria进行复杂查询。
Bean对应单表。
Action中通过

```java
		App.getHibernateTransactionTemplate().execute(new TransactionCallback() {
			public Object doInTransaction(TransactionStatus ts) {
				try {
					trans.run();
				} catch (Throwable e) {
					ts.setRollbackOnly();
					trans.setTransactionException(new TransactionException(e));
				}
				return null;
			}
		});
		TransactionException e = trans.getTransctionException();
		if (e != null)
			throw e;
```

    <!--hiberate事务管理器-->
    <bean id="hibernateTransactionManager" class="org.springframework.orm.hibernate3.HibernateTransactionManager">
      <property name="sessionFactory">
        <ref bean="sessionFactory" />
      </property>
    </bean>
    <!-- hiberate事务模板-->
    <bean id="hibernateTransactionTemplate" class="org.springframework.transaction.support.TransactionTemplate">
      <property name="transactionManager">
        <ref bean="hibernateTransactionManager" />
      </property>
    </bean>
的方式进行事务处理。

**Spring的编程式事务管理**

### 2013框架

Controller  <-->  Service  <--> Dao  <-->  Entity

Entity对应单表。
Dao使用JPA方式，定义接口，JPA自动实现，复杂查询采用nativeQuery方式。
Service层中通过@Transactional 标签处理事务。多表联合查询使用JdbcTemplate或者EntityManager实现。
Cntroller层调用Service完成业务处理。

**Spring的声明式事务管理**

## ORM（Hibernate VS JPA）

### 海事框架采用Hibernate
支持使用Hibernate DetachedCriteria进行复杂查询。



### 2013框架采用HibernateJPA



## 事务
海事框架采用Spring的编程式事务管理
2013框架采用Spring的声明式事务管理

# 2013框架特色

## 页面参数
查询数据主要绑定在数据模型中，每个查询设定其查询名称为Q_查询方式_查询属性。分页数据以P_形式进行设定；

|功能        |参数名                |说明|
|----        |----                  |----|
|查询        |Q\_EQ\_属性名         |等价于SQL中的“=”|
|            |Q\_LIKE\_属性名       |等价于SQL中的“like”|
|            |Q\_GT\_属性名         |等价于SQL中的“>”|
|            |Q\_LT\_属性名         |等价于SQL中的“<”|
|            |Q\_GTE\_属性名        |等价于SQL中的“>=”|
|            |Q\_LTE\_属性名        |等价于SQL中的“<=”|
|            |Q\_NULL\_属性名       |等价于SQL中的“is null”|
|            |Q\_BLANK\_属性名      |等价于SQL中的“= ‘’”|
|            |Q\_NNULL\_属性名      |等价于SQL中的“is not null”|
|            |Q\_NBLANK\_属性名     |等价于SQL中的“!= ‘’”|
|分页        |P\_orders             |排序参数名称（排序字段,[排序字段,排序方式],[排序字段]）|
|            |P\_pageNumber         |当前页号参数名称（从1开始计数）|
|            |P\_pagesize           |每页记录数参数名称|
|属性过滤    |F[\_过滤器ID]\_in      |设定要获取的数据字段及其顺序；过滤器ID，以实体中JsonFilter注解中的名称对应|
|            |F[\_过滤器ID]\_out    |设定要排除的数据字段|
|数据处理    |E\_model\_name        |数据模型模版参数名称|
|            |E\_entity\_class      |实体类参数名称|
|工作流参数  |CF\_rd                 |刷新关联数据|
|            |op                    |操作类型|
|            |。。。                |更多参数请查看CoflowEntity实体|

页面参数在调用默认search方法时，会自动调用processSearch(); 达到按照上面说明进行数据查询。
另外，可以通过向Controller的initParameters里面添加页面参数的形式，添加一些特殊的查询条件。
这时最前面的Q\_不需要。

    this.initParameters.put("EQ_unitId", unitId);

## Spring security集成

Spring security是一个网站安全框架。和Apache Shiro类似，可以把网站安全相关内容从业务代码中分离出来。开发时先进行业务开发，然后加入权限标签；或者分别由不同团队负责权限以及业务等。非常便于开发和后期维护。

[使用 Spring Security 保护 Web 应用的安全](https://www.ibm.com/developerworks/cn/java/j-lo-springsecurity/)
[Spring Security参考手册](https://vincentmi.gitbooks.io/spring-security-reference-zh/content/1_introduction.html)


## Sitemesh应用

应用Sitemesh进行页面布局。

    SiteMesh is a web-page layout system that can be used to abstract common look and feel from the functionality of a web-application and to assemble large webpages from smaller components. Pages and components can have meta-data extracted from them (such as body, title and meta-tags) which can be used by decorators (skins) that are applied.

* 是一个Web页面布局、装饰以及与现有Web应用集成的框架。有助于在由大量页面构成的项目中创建一致的页面布局和外观、一致的导航条、一致的布局方案等。
* 截取对Web服务器的任何静态或动态页面的请求，解析页面，从内容中获得属性和数据，生成对原页面进行修改后的最终页面——基于装饰模式
* 此外可以以面板（Panel）的形式，将完整的HTML页面包含在另一个页面中——类似于服务器端包含。使用此功能，可以非常快速和有效的创建门户网站类型的Web站点。这基于知名的组合模式。

具体应用为：
修改 WEB-INF/decorators.xml，指定合适的装饰页面，配置不需要被装饰的路径。然后开发对应的业务页面时可以暂时忘记有装饰页面这件事情，专注于自己的业务即可。


# 使用2013框架建立项目步骤
1. 复制2013框架示例项目到新的项目，更改项目名称
1. 修改web.xml 的 webAppRootKey
1. 删掉不要的代码
1. 修改数据库配置文件 conf/db
1. 修改装饰页面
1. 修改登录页面
1. 根据表定义Entity
1. 建立DAO、Service、Controller
1. 建立jsp文件
1. 测试是否正常显示
