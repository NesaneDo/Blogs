

# Spring Boot + Mybatis-Plus 启动项目失败，Error creating bean with name 'xxx': Injection of resource dependencies failed

```xml
Error creating bean with name 'doctorAccountController': Injection of resource dependencies failed; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'doctorAccountServiceImpl': Unsatisfied dependency expressed through field 'baseMapper'; nested exception is org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'doctorAccountMapper' defined in file [E:\Programming\Products\2021\HeadacheWeb\SpringBoot\headache\target\classes\com\xd\headache\mapper\DoctorAccountMapper.class]: Invocation of init method failed; nested exception is java.lang.IllegalArgumentException: Property 'sqlSessionFactory' or 'sqlSessionTemplate' are required
```



> 注意事项

1. 检查配置文件是否正确

```properties
mybatis-plus.mapper-locations=classpath:/com/xx/xxx/mapper/*.xml 	# mapper 文件位置
mybatis-plus.type-aliases-package=com.xx.xxx.entity 				# 实体类位置
```

2. 检查 `Mybatis-Plus` 配置是否正确，`basePackages` 应该到 `mapper `文件的上一级目录，而不是 `xxx.mapper.*`

   ```java
   @Configuration
   @MapperScan(annotationClass = Repository.class, basePackages = "com.xd.headache.mapper")
   public class MybatisPlusConfig {
   
       @Bean
       public MybatisPlusInterceptor mybatisPlusInterceptor() {
           MybatisPlusInterceptor interceptor = new MybatisPlusInterceptor();
           interceptor.addInnerInterceptor(new PaginationInnerInterceptor(DbType.MYSQL));
           return interceptor;
       }
   }
   ```

   