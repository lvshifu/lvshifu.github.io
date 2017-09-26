---
title: Ionic笔记1--Node介绍
date: 2017-04-05 21:18:02
tags:
  - Node
  - Ionic
categories:
---

# 从JAVA开发者角度看Node
<!--more-->

[NodeJS 对于 Java 开发者而言是什么？](http://www.codeceo.com/article/what-nodejs-for-java-developer.html)

[NPM-node.js界的maven 入门](http://blog.csdn.net/liuyuqin1991/article/details/73174230)


# 常用命令
## 查看所有高级的npm moudles

npm list --depth=0

## 查看所有全局安装的模块

npm list --depth=0 -global

## NPM代理
1. 方法一：
.npmrc 文件上直接设置代理：registry=https://registry.npm.taobao.org

1. 方法二：
 * 临时代理：
 npm install ionic --registry=https://registry.npm.taobao.org
 * 全局配置：
 npm config set registry https://registry.npm.taobao.org

## 查看NPM配置
npm config list

## Ionic start 命令会下载很多东西，太慢，加代理

1. set proxy=http://127.0.0.1:1645   （lantern代理地址，可修改为其他地址）
1. ionic start LeftRightMenu sidemenu
