# Druid+Mybatis-plus+Spring Boot 项目查询时报错 SQLFeatureNotSupportedException null

报错信息：

```xml
java.sql.SQLFeatureNotSupportedException: null
	at com.alibaba.druid.pool.DruidPooledResultSet.getObject(DruidPooledResultSet.java:1771) ~[druid-1.1.6.jar:1.1.6]
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:1.8.0_271]
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[na:1.8.0_271]
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:1.8.0_271]
	at java.lang.reflect.Method.invoke(Method.java:498) ~[na:1.8.0_271]
	at org.apache.ibatis.logging.jdbc.ResultSetLogger.invoke(ResultSetLogger.java:69) ~[mybatis-3.5.6.jar:3.5.6]
	at com.sun.proxy.$Proxy149.getObject(Unknown Source) ~[na:na]
	at org.apache.ibatis.type.LocalDateTimeTypeHandler.getNullableResult(LocalDateTimeTypeHandler.java:38) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.type.LocalDateTimeTypeHandler.getNullableResult(LocalDateTimeTypeHandler.java:28) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.type.BaseTypeHandler.getResult(BaseTypeHandler.java:85) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.resultset.DefaultResultSetHandler.applyAutomaticMappings(DefaultResultSetHandler.java:560) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.resultset.DefaultResultSetHandler.getRowValue(DefaultResultSetHandler.java:402) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.resultset.DefaultResultSetHandler.handleRowValuesForSimpleResultMap(DefaultResultSetHandler.java:354) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.resultset.DefaultResultSetHandler.handleRowValues(DefaultResultSetHandler.java:328) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.resultset.DefaultResultSetHandler.handleResultSet(DefaultResultSetHandler.java:301) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.resultset.DefaultResultSetHandler.handleResultSets(DefaultResultSetHandler.java:194) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.statement.PreparedStatementHandler.query(PreparedStatementHandler.java:65) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.statement.RoutingStatementHandler.query(RoutingStatementHandler.java:79) ~[mybatis-3.5.6.jar:3.5.6]
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:1.8.0_271]
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[na:1.8.0_271]
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:1.8.0_271]
	at java.lang.reflect.Method.invoke(Method.java:498) ~[na:1.8.0_271]
	at org.apache.ibatis.plugin.Plugin.invoke(Plugin.java:63) ~[mybatis-3.5.6.jar:3.5.6]
	at com.sun.proxy.$Proxy146.query(Unknown Source) ~[na:na]
	at com.baomidou.mybatisplus.core.executor.MybatisSimpleExecutor.doQuery(MybatisSimpleExecutor.java:69) ~[mybatis-plus-core-3.4.2.jar:3.4.2]
	at org.apache.ibatis.executor.BaseExecutor.queryFromDatabase(BaseExecutor.java:325) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.executor.BaseExecutor.query(BaseExecutor.java:156) ~[mybatis-3.5.6.jar:3.5.6]
	at com.baomidou.mybatisplus.core.executor.MybatisCachingExecutor.query(MybatisCachingExecutor.java:165) ~[mybatis-plus-core-3.4.2.jar:3.4.2]
	at com.baomidou.mybatisplus.extension.plugins.MybatisPlusInterceptor.intercept(MybatisPlusInterceptor.java:81) ~[mybatis-plus-extension-3.4.2.jar:3.4.2]
	at org.apache.ibatis.plugin.Plugin.invoke(Plugin.java:61) ~[mybatis-3.5.6.jar:3.5.6]
	at com.sun.proxy.$Proxy145.query(Unknown Source) ~[na:na]
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:147) ~[mybatis-3.5.6.jar:3.5.6]
	at org.apache.ibatis.session.defaults.DefaultSqlSession.selectList(DefaultSqlSession.java:140) ~[mybatis-3.5.6.jar:3.5.6]
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:1.8.0_271]
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[na:1.8.0_271]
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:1.8.0_271]
	at java.lang.reflect.Method.invoke(Method.java:498) ~[na:1.8.0_271]
	at org.mybatis.spring.SqlSessionTemplate$SqlSessionInterceptor.invoke(SqlSessionTemplate.java:426) ~[mybatis-spring-2.0.5.jar:2.0.5]
	at com.sun.proxy.$Proxy68.selectList(Unknown Source) ~[na:na]
	at org.mybatis.spring.SqlSessionTemplate.selectList(SqlSessionTemplate.java:223) ~[mybatis-spring-2.0.5.jar:2.0.5]
	at com.baomidou.mybatisplus.core.override.MybatisMapperMethod.executeForIPage(MybatisMapperMethod.java:122) ~[mybatis-plus-core-3.4.2.jar:3.4.2]
	at com.baomidou.mybatisplus.core.override.MybatisMapperMethod.execute(MybatisMapperMethod.java:86) ~[mybatis-plus-core-3.4.2.jar:3.4.2]
	at com.baomidou.mybatisplus.core.override.MybatisMapperProxy$PlainMethodInvoker.invoke(MybatisMapperProxy.java:148) ~[mybatis-plus-core-3.4.2.jar:3.4.2]
	at com.baomidou.mybatisplus.core.override.MybatisMapperProxy.invoke(MybatisMapperProxy.java:89) ~[mybatis-plus-core-3.4.2.jar:3.4.2]
	at com.sun.proxy.$Proxy80.selectPage(Unknown Source) ~[na:na]
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:1.8.0_271]
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[na:1.8.0_271]
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:1.8.0_271]
	at java.lang.reflect.Method.invoke(Method.java:498) ~[na:1.8.0_271]
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:344) ~[spring-aop-5.3.4.jar:5.3.4]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:198) ~[spring-aop-5.3.4.jar:5.3.4]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163) ~[spring-aop-5.3.4.jar:5.3.4]
	at org.springframework.dao.support.PersistenceExceptionTranslationInterceptor.invoke(PersistenceExceptionTranslationInterceptor.java:137) ~[spring-tx-5.3.4.jar:5.3.4]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:186) ~[spring-aop-5.3.4.jar:5.3.4]
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:215) ~[spring-aop-5.3.4.jar:5.3.4]
	at com.sun.proxy.$Proxy81.selectPage(Unknown Source) ~[na:na]
	at com.baomidou.mybatisplus.extension.service.IService.page(IService.java:298) ~[mybatis-plus-extension-3.4.2.jar:3.4.2]
	at com.baomidou.mybatisplus.extension.service.IService.page(IService.java:308) ~[mybatis-plus-extension-3.4.2.jar:3.4.2]
	at com.baomidou.mybatisplus.extension.service.IService$$FastClassBySpringCGLIB$$f8525d18.invoke(<generated>) ~[mybatis-plus-extension-3.4.2.jar:3.4.2]
	at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:218) ~[spring-core-5.3.4.jar:5.3.4]
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:688) ~[spring-aop-5.3.4.jar:5.3.4]
	at com.xd.headache.service.impl.PatBasicInfoServiceImpl$$EnhancerBySpringCGLIB$$d7b2c915.page(<generated>) ~[classes/:na]
	at com.xd.headache.api.PatBasicInfoController.getPagePatients(PatBasicInfoController.java:63) ~[classes/:na]
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:1.8.0_271]
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[na:1.8.0_271]
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:1.8.0_271]
	at java.lang.reflect.Method.invoke(Method.java:498) ~[na:1.8.0_271]
	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:197) ~[spring-web-5.3.4.jar:5.3.4]
	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:141) ~[spring-web-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:106) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:894) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:808) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:87) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1060) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:962) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1006) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:898) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:626) ~[tomcat-embed-core-9.0.43.jar:4.0.FR]
	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:883) ~[spring-webmvc-5.3.4.jar:5.3.4]
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:733) ~[tomcat-embed-core-9.0.43.jar:4.0.FR]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:227) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53) ~[tomcat-embed-websocket-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.springframework.web.filter.CorsFilter.doFilterInternal(CorsFilter.java:91) ~[spring-web-5.3.4.jar:5.3.4]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119) ~[spring-web-5.3.4.jar:5.3.4]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:100) ~[spring-web-5.3.4.jar:5.3.4]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119) ~[spring-web-5.3.4.jar:5.3.4]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.springframework.web.filter.FormContentFilter.doFilterInternal(FormContentFilter.java:93) ~[spring-web-5.3.4.jar:5.3.4]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119) ~[spring-web-5.3.4.jar:5.3.4]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:201) ~[spring-web-5.3.4.jar:5.3.4]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:119) ~[spring-web-5.3.4.jar:5.3.4]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:189) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:162) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:202) ~[tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:97) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:542) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:143) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:92) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:78) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:346) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:374) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:65) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:887) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1684) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149) [na:1.8.0_271]
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624) [na:1.8.0_271]
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61) [tomcat-embed-core-9.0.43.jar:9.0.43]
	at java.lang.Thread.run(Thread.java:748) [na:1.8.0_271]

```



移除 代码生成 相关的依赖：

```xml
<!--        <dependency>-->
<!--            <groupId>com.baomidou</groupId>-->
<!--            <artifactId>mybatis-plus-generator</artifactId>-->
<!--            <version>3.1.2</version>-->
<!--        </dependency>-->
<!--        <dependency>-->
<!--            <groupId>org.freemarker</groupId>-->
<!--            <artifactId>freemarker</artifactId>-->
<!--            <version>2.3.30</version>-->
<!--        </dependency>-->
```

将 druid、mybatis-plus的相关依赖修改如下

```xml
<dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.1.21</version>
        </dependency>
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
            <version>3.1.1</version>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-typehandlers-jsr310</artifactId>
            <version>1.0.1</version>
        </dependency>
        <dependency>
            <groupId>com.fasterxml.jackson.datatype</groupId>
            <artifactId>jackson-datatype-jsr310</artifactId>
            <version>2.9.2</version>
        </dependency>
```

注意后两个依赖，一定要加，不然也会错