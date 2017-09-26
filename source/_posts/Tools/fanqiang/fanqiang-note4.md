---
title: 科学上网笔记4--Shadowsocks
date: 2014-08-06 21:18:02
tags:
  - 科学上网
  - 影梭
  - Shadowsocks
categories: 
---
# Shadowsocks
中文名称影梭，有PC和Android版本。是SSH隧道技术的升级版。

ssh tunnel 代理，通过 ssh 与墙外服务器建立一条加密隧道，用户通过建立起的隧道进行代理，通过 ssh server 向真实的服务发起请求，服务通过 ssh server，再通过创建好的隧道返回给用户，此时的通讯 GFW 会将其视作普通的连接。达到访问墙外网站的目的。但由于创建隧道和数据传输的过程中，ssh 本身的特征是明显的，GFW 通过各种流量特征分析，能够识别哪些连接是 ssh 隧道，并对隧道做干扰。应对与这种情况，出现了Shadowsocks技术。

Shadowsocks 把原来 ssh 创建的 Socks5 协议拆开成 Server 端和 Client 端，它发出的 TCP 包，没有明显包特征，GFW 分析不出来。