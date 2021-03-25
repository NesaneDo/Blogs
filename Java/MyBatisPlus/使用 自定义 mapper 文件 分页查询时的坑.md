# 使用 自定义 mapper 文件 分页查询时的坑

> 背景：在使用自定义 mapper 文件写 sql，但使用 MyBatis-plus 的分页功能时发现拼接的 sql 不对

在 mapper 中的 sql 如下：

```xml
SELECT * FROM t_user WHERE state = #{state};
```

在接口 mapper 中方法定义如下：

```java
IPage<User> getPagedStatedUsers(IPage<User> page,int state);
```

打印日志时发现拼接的 sql 如下：

```xml
SELECT id,name,state FROM t_user WHERE state = ?; LIMIT 10
```

> **总结：在 自定义 mapper 文件中写 sql 时不要加 "`;`"**