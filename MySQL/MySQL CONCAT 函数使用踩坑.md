# MySQL CONCAT 函数使用踩坑

​	CONCAT 函数是用来拼接字符串的，使用中要注意：

1. 当拼接的参数中存在 NULL 时，则拼接结果为 NULL

   ```mysql
   select CONCAT(1234,NULL);
   -- 结果 NULL
   ```

   

2. 与空串拼接不会为NULL

   ```mysql
   select CONCAT(1234,'');
   -- 结果 '1234'
   ```

   