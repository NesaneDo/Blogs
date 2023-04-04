# MyBatis Plus DynamicDataSourceContextHolder push 一个不存在的数据源

当使用 `DynamicDataSourceContextHolder.push(ds)` ，其中 **`ds`** 没有配置在动态数据源中时，最终使用的是 **默认数据源**，可以使用 `DynamicDataSourceContextHolder.peek()` 确认 

