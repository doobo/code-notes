# 很好用的一种Http工具
主要介绍在Java编码中，对使用http的个人见解

## 网页代理
如何几行代码，代理一个静态网页，举一反三，做成更通用的代理方法

## API代理
简单的一个Controller，就可以代理整个API请求，废弃Nginx代理，还可以集成各种监控日志
```
https://5fu8.com/search.json
http://localhost:8080/api/proxy/search.json
```
相关Maven依赖
```xml
<dependency>
   <groupId>com.github.doobo</groupId>
   <artifactId>okhttp-tools</artifactId>
   <version>1.3</version>
</dependency>
```