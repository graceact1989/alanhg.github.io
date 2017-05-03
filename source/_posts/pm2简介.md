---
title: pm2简介
abbrlink: 8ab7c90a
date: 2016-09-19 21:37:13
tags:
    - node
    - pm2
---
pm2 是一个带有负载均衡功能的Node应用的进程管理器.
当你要把你的独立代码利用全部的服务器上的所有CPU，并保证进程永远都活着，0秒的重载， PM2是完美的。它非常适合IaaS结构，但不要把它用于PaaS方案（随后将开发Paas的解决方案）.
*如果你还是在用node app.js启动,那你太low了,赶紧使用pm2吧!*
备注：SaaS、PaaS和IaaS是云服务模式。
        SaaS 软件即服务，例如Google的 Gmail 邮箱服务.面向应用型用户.
        PaaS 平台即服务.例如Google的GAE,面向开发型用户
        IaaS  基础架构即服务,例如亚马逊的AWS，IaaS对于不知道新推出的应用程序/网站会有多成功的创业公司来说非常有用

主要特性：
内建负载均衡（使用Node cluster 集群模块）
后台运行
0秒停机重载，我理解大概意思是维护升级的时候不需要停机.
具有Ubuntu和CentOS 的启动脚本
停止不稳定的进程（避免无限循环）
控制台检测
提供 HTTP API
远程控制和实时的接口API ( Nodejs 模块,允许和PM2进程管理器交互 )

测试过Nodejs v0.11 v0.10 v0.8版本，兼容CoffeeScript,基于Linux 和MacOS.

**pm2相关命令一览**
```
$ npm install pm2 -g            # Install PM2
$ pm2 start app.js              # Start, Daemonize and auto-restart application
$ pm2 start app.js -i 4         # Start 4 instances of application in cluster mode
                                # it will load balance network queries to each app
$ pm2 start app.js --name="api" # Start application and name it "api"
$ pm2 start app.js --watch      # Restart application on file change
$ pm2 start script.sh           # Start bash script
$ pm2 start npm -- start        # Start, Daemonize and auto-restart Node application

$ pm2 list                      # List all processes started with PM2
$ pm2 monit                     # Display memory and cpu usage of each app
$ pm2 show [app-name]           # Show all informations about application

$ pm2 logs                      # Display logs of all apps
$ pm2 logs [app-name]           # Display logs for a specific app
$ pm2 flush

$ pm2 stop all                  # Stop all apps
$ pm2 stop 0                    # Stop process with id 0
$ pm2 restart all               # Restart all apps
$ pm2 reload all                # Reload all apps in cluster mode
$ pm2 gracefulReload all        # Graceful reload all apps in cluster mode
$ pm2 delete all                # Kill and delete all apps
$ pm2 delete 0                  # Delete app with id 0
$ pm2 scale api 10              # Scale app with name api to 10 instances
$ pm2 reset [app-name]          # Reset number of restart for [app-name]

$ pm2 startup                   # Generate a startup script to respawn PM2 on boot
$ pm2 save                      # Save current process list
$ pm2 resurrect                 # Restore previously save processes
$ pm2 update                    # Save processes, kill PM2 and restore processes
$ pm2 generate                  # Generate a sample json configuration file

$ pm2 deploy app.json prod setup    # Setup "prod" remote server
$ pm2 deploy app.json prod          # Update "prod" remote server
$ pm2 deploy app.json prod revert 2 # Revert "prod" remote server by 2

$ pm2 module:generate [name]    # Generate sample module with name [name]
$ pm2 install pm2-logrotate     # Install module (here a log rotation system)
$ pm2 uninstall pm2-logrotate   # Uninstall module
$ pm2 publish                   # Increment version, git push and npm publish
```

**开启进程的不同方式**
```
$ pm2 start app.js --watch      # Restart application on file change
$ pm2 start script.sh           # Start bash script
$ pm2 start app.js -- -a 34     # Start app and pass option -a 34
$ pm2 start app.json            # Start all applications declared in app.json
$ pm2 start my-python-script.py --interpreter python
```

**列出所有的执行进程**
```
$ pm2 list
```

更多具体细节及版本信息、源码请登录github<https://github.com/Unitech/pm2>