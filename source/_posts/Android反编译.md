---
title: Android反编译
abbrlink: 792a6dc0
date: 2017-03-13 08:26:53
tags:
---
由于需要，进行了反编译的学习，做了几次有点认识,及时总结下。

### 反编译需要用到工具

- http://www.decompileandroid.com/
  http://www.javadecompilers.com/apk 去壳，反编译
- Charles、Fiddler,抓包
- Android Studio，阅读项目代码

### 关于反编译说明

— 目前安卓开发，在打包时候都是会进行**代码混淆**的，所以即使去壳反编译后，也不是说就完全的展示了项目的情况，但是基本上并不影响大体的阅读。
其实反编译一些优秀的app，阅读别人的代码，了解别人的整体设计，是种很不错的学习形式。
— 现在apk反编译已经有web在线形式的了，经过测试，我觉得上面的两个尤其**decompileandroid**做的还不错，尽可能的换原来项目原来的情况。
  其实目前的反编译工具，背后用的工具都是大同小异的，背后用到的工具是这几个dex2jar，JAD - Java Descompiler，apktool,zip/unzip
- 前端本身是透明的，所以反编译用来学习很好，不要直接盗窃别人的劳动成果，这点是需要注意的。
