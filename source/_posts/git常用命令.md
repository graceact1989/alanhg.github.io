---
title: git常用命令
abbrlink: 423abe9e
date: 2017-05-05 23:22:37
tags:
---

# 前言
想玩好Github开源项目，不懂git不行，所以这里记录下，在使用中，用到的一些命令，方便自己以后去反复记忆，同时也希望能帮到一些朋友。

主要的命令记住，方便操作，其余的会查询即可。

# 命令
以实际例子来说明，我在实际使用中用到的一些命令
```

#取github上仓库的某个分支
git clone -b source git@github.com:heqiang421/heqiang421.github.io.git

git status
git commit -m 'message'

#提交修改
git push


```
# 常见错误
## Git: fatal: Pathspec is in submodule
 解决办法：
  ```
   git rm --cached directory
   git add directory
  
  ```


# 辅助资料

+ [常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)