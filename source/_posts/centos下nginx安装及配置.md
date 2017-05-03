---
title: centos下nginx安装及配置
author: Qiang He
tags:
  - 技术
  - nginx
  - centos
abbrlink: 37016
date: 2016-09-10 09:14:03
---
最近在搭建一个web站点,为了提高用户访问网页的加载速度,想到了gzip,进而之找到了nginx,nginx是一个高性能的http与反向代理服务器,
Gzip开启以后会将输出到用户浏览器的数据进行压缩的处理，这样就会减小通过网络传输的数据量，提高浏览的速度。
**下面贴出安装nginx的命令及nginx的启动,停止,重启命令**
```
rpm -ivh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
yum -y install nginx
nginx
nginx –s stop
nginx –s reload
```
**下面贴出在nginx.conf配置文件中配置gzip的基本信息**
```  
# 开启gzip
gzip on;
``
# 启用gzip压缩的最小文件，小于设置值的文件将不会压缩
gzip_min_length 1k;

# gzip 压缩级别，1-10，数字越大压缩的越好，也越占用CPU时间，后面会有详细说明
gzip_comp_level 2;

# 进行压缩的文件类型。javascript有多种形式。其中的值可以在 mime.types 文件中找到。
gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;

# 是否在http header中添加Vary: Accept-Encoding，建议开启
gzip_vary on;

# 禁用IE 6 gzip
gzip_disable "MSIE [1-6]\.";
```