---
title: linux常用命令
tags:
  - linux
abbrlink: fe4ef317
date: 2017-05-15 15:40:41
---

## 查看系统信息

```
uname -a # 查看内核，操作系统，CPU信息 
head -n 1 /etc/issue   # 查看操作系统版本
env # 查看环境变量

```
## 账户权限
```
# 修改当前用户密码
$ passwd
```
## 文件操作

```
vi filename
cat filename

# 删除文件
$ rm filename

# 删除文件夹
$ rm -rf dir

# 查找并删除
$ find  .  -name test  | xargs rm -rf   

# 压缩
$ tar zcvf FileName.tar.gz DirName

# 解压
$ tar zxvf FileName.tar.gz
```
## 目录操作

```
# 当前用户目录下
$ cd ~
```