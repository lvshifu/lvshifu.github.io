---
title: 翻墙笔记2--plink
date: 2011-05-06 21:18:02
tags:
  - 翻墙
  - SSH Tunnel
  - plink
categories: 
---
# plink
plink -N userid@ssh.sshcenter.info -D 127.0.0.1:7070 -pw password

<!--more-->

# linux命令
ssh -qTfnN -D 7070 username@remote-host


# Bitvise Tunnelier配置
## Login页面
Host填入服务器ip，Port填写端口，然后填入Username和Password。
## Options页面
On Login的Open Terminal和Open SFTP取消勾选。
## Service页面
Socks / HTTP Proxy  Forwarding的Enabled勾选，Listen Port输入7070。


SSH翻墙通常使用Bitvise Tunnelier，有独立客户端，使用方便。但是如果是想使用终端命令的话，Windws可使用putty系列的plink。