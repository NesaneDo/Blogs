# Thymeleaf 动态改变 class 样式

在 Thymeleaf 中如何根据后端的数据对样式进行动态改变呢？

可以使用将改变前后都需要的公共样式使用普通属性 `class` ，将需要动态改变的样式使用 `th:classappend`

如：  

```html
<span th:text="${res.getMsg()}" th:classappend="${res.getCode()==1?'text-green':'text-light-red'}" class="w100p text-center margin-b-16"></span>
```

