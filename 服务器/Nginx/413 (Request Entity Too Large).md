# 413 (Request Entity Too Large)

使用 `Nginx` 配置后出现此错误：请求实体过大。

**解决办法：**

在相应 `server{}` 中 添加

``` xml
client_max_body_size 4m; # 上传文件最大不超过 4 MB
```



