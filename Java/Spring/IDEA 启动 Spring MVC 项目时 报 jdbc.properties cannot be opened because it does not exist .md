# IDEA 启动 Spring MVC 项目时 报 jdbc.properties cannot be opened because it does not exist 

```xml
<!--引入properties文件-->
    <context:property-placeholder location="classpath*:jdbc.properties"/>
```

**解决方法：**

> 在 **classpath** 后添加 **`*`** 