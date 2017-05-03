title: ionic2中引入D3
abbrlink: 1a57766f
date: 2017-02-03 13:47:26
tags:
---

图表解决方案，主要还是使用echarts，但是并不能满足所有的需要，对于如气泡这种展现形式，需要用到d3
ionic2中引用d3,方式如下
```
//宿主index页面中导入对应的js文件
<script src="assets/d3.min.js"></script>

//在需要使用到的组件中进行声明即可
declarlet d3: any;
```


