---
title: ionic2开发说明
abbrlink: 238255b8
date: 2017-03-20 22:55:09
tags:
---

# ionic2

ionic2是利用cordova框架来访问硬件底层，本身使用web开发形式来进行开发，所以对于web开发人员来说较为简单的。
ionic2与ionic1相比，其实可以理解为是背后ng的进步，ionic1用的是ng1，ionic2用的是ng2,要想开发效率更高，把ng2学好，就简单多了。
目前现状，学习ionic1已经没有必要，2已经成熟了，如果可能未来还需要把老的项目重写为ionic2，因为2的维护性更高。

## 常见问题

+ ionic成熟度
  上Github上去看ionic,已经2万多星星了，其实这个也能够说明社区很活跃，所以本身已经是成熟的框架技术了，我本人也用ionic1,及目前的2开发了不下5款APP。
  对于小项目，完全试用，遇到的问题基本都可以找到解决办法。
  
+ 性能如何
  AOT打包后，ionic2的app包并不大，运行性能对于普通app来说足够了，目前ionic2版本是V2.2，过几天2.3应该就出来，现在性能相对1来说，进步非常明显了。
  所以小APP项目开发没有问题。
  目前问题在于启动白屏时间过长，这个应该需要等到angular推出ng4之后，ionic2的跟进了,判断会在5月份了，因为ng4会在3月底和4月初出来。
  
+ 如何学习
  想玩好，重点在于*ng2*的学习和*ts*的基本学习，两者都玩会了，玩ionic2,照着官网来做，so easy。* 官方资料才是一手资料 *，
  - https://github.com/angular/angular
  - https://angular.io/docs/ts/latest/
  - https://github.com/driftyco/ionic
  - http://ionicframework.com/docs/
  
+ 支持AOT否
  
  YES，官方支持
  ```
    npm run android --prod #prod参数加上后，就会进行ngc编译，打包出来就是AOT包，对比大小及看控制台输出就可以看出
   ```
