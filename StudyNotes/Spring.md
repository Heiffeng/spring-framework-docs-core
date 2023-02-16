

# 依赖注入

构造器注入的优缺点
Setter注入的优缺点

构造器注入和Setter怎么选？


循环依赖问题

构造器注入不会存在循环依赖问题，因为会报错。
Setter注入可以避免循环依赖问题，具体做法是引用初始化的bean，即半成品bean。

为什么Setter注入能避免循环依赖问题
https://www.jianshu.com/p/80495485984f