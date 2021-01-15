# Spring boot Thymeleaf 结合 Layui 使用报错 Could not parse as expression

主要错误是在使用 `Layui`中 数据表格 `table` 中的 `cols`，

设置表头时使用的 **`[[]]`**,这样的表示方法会被 **`thymeleaf`** 认作内联表达式

解决方法：将两对中括号分开，如

```html
[
	[
		{...}
	]
]
```

