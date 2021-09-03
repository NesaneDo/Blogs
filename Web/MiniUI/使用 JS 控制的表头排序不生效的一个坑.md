# MiniUI 使用 JS 控制的表头排序不生效的一个坑

在字段上添加 `allowSort = 'true'`，想使其排序，结果不生效，如下代码:

```javascript
{field:'res',header:'结果',width:32,headerAlign:'center',
					align:'center',renderer:'resFlagRenderer',allowSort:'true'}
```

**解决：**

改为 `allowSort = true`，去掉引号即可，如下

```javascript
{field:'res',header:'结果',width:32,headerAlign:'center',
					align:'center',renderer:'resFlagRenderer',allowSort:true}
```



### 总结：

使用引号将会被解析成字符串，而非 bool 类型。大意了！