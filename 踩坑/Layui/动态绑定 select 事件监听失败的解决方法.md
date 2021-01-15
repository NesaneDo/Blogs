# 动态绑定 select 事件监听失败的解决方法

有以下几个地方需要注意：

1. 检查select是否不在 layui-form 的标签之下
2. 检查 select 是否添加了 lay-filter 属性
3. 检查 select 是否添加了 lay-ignore 属性，lay-ignore 将会完全将 select 组件变成一般的