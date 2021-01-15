# Thymeleaf 在 JavaScript 中使用模板变量

thymeleaf 在 html 中使用 java 变量的方式是：

在后台程序中对变量赋值：

```java
@GetMapping("test")
public String test(Model model){
    model.addAttribute("var","This is a string."); // 添加变量和值
    return "test"; // 返回视图
}
```

则可以在 html 视图中使用如下方式获取：

```html
<span th:text="${var}"></span>
```

则 thymeleaf 会将 **`This is a String.`** 渲染到 span 中。

在 javascript 中获取变量则可以使用：

```javascript
<script th:inline="javascript">
    console.log([[${var}]])
</script>
```

使用 **`[[]]`** 来包裹即可