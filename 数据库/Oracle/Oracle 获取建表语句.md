# Oracle 获取建表语句

```oracle
select dbms_metadata.get_ddl('TABLE','<TABLE_NAME>') from <DATABASE_NAME>;

<TABLE_NAME> 表名，必须使用大写
<DATABASE_NAME> 库名
```



