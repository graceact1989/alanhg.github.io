---
title: redis使用介绍
abbrlink: 1e2fb0dc
date: 2017-05-24 11:38:20
tags:
- redis
---
## 简介

[Redis](https://zh.wikipedia.org/wiki/Redis)是一个使用ANSI C编写的开源、支持网络、基于内存、可选持久性的键值对存储数据库。

## 相关操作
```
# yum安装
$ yum install -y redis

# 简单 形式启动
$ redis-server /etc/redis.conf
# 服务形式启动
$ service start redis

# 进入CLI
$ redis-cli

# 服务自启动
$ chkconfig redis on   

```
## 其它

+ 配置文件[下载](http://download.redis.io/redis-stable/redis.conf)
    