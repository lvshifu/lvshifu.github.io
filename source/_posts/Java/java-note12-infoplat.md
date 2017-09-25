---
title: Java笔记12--信息发布平台加访问限制问题
date: 2017-09-14 13:24:03
tags: [Java,Apache,Nginx]
categories: 
---
# 问题
在检察院业务中，内网发布基本使用信息发布平台，但是检察院业务有个通用的需求，

    发布信息要加入权限区分
    有些内容是全市检察院可查看的
    有些内容是相关检察院可查看的
    有些内容是仅供本院查看的

在老的信息发布平台上，目录页是JSP，可以很容易的在后台判断访问者IP为多少，进而输出不同的目录页。
<!--more-->

新的信息发布平台上，全部内容均为静态Html页面，要实现相应的功能就不太方便了。
结合客户的需求，对应有两个解决方案。

# 方案1
使用Apache做前端，拿掉信息发布平台默认的前端nginx，信息发布平台生成静态Html页面时，设置页面的访问权限，根据设置的访问权限，生成不同的.htaccess文件，在.htaccess文件里面加入IP限制的内容。

```    
order allow,deny
allow from 10.1
allow from 10 172.20 192.168.2
allow from 10.0.0.0/24
deny from all

ErrorDocument 403 "此页面仅限XXX内部访问！"
```


方案1在有些检察院运行正常，但是在部分检察院出现访问速度慢的现象。

# 方案2
使用Nginx做前端，信息发布平台生成静态Html页面时，设置页面的访问权限，根据设置的访问权限，在通常生成的目录下，生成不同的子目录，比如Level1、Level2、Level3、Level4，分别对应不同的访问权限。
利用nginx对URL的解析，针对URL里面字符串设置不同的访问权限。

nginx配置文件里增加

```
location /Level1/ {
  allow   192.168.1.0/24;
  deny    all;
}

location /Level2/ {
  allow   192.168.1.0/24;
  allow   192.168.2.0/24;
  deny    all;
}

location /Level3/ {
  allow   192.168.1.0/24;
  allow   192.168.2.0/24;
  allow   192.168.3.0/24;
  deny    all;
}
```

