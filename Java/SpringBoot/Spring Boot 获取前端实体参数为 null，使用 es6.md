# Spring Boot 获取前端实体参数为 null，使用 es6

比如有如下 JS 程序：

```javascript
$.post("deleteUser",{user},res=>{ // user 为 {name:'张三',age:18}
    console.log(res)
})
```

后台：

```java
@PostMapping("deleteHolder")
@ResponseBody
public Map<String, Object> deleteUser(User user) {
    System.out.println(user); // null
    boolean res=userService.deleteUser(user);
    if(res)logDelete(user.toString());
    return resDelete(res);
}
```

这样取不到值的解决办法：

修改 JS 代码

```javascript
$.post("deleteUser",{user:user},res=>{ // user 为 {name:'张三',age:18}
    console.log(res)
})
```

或者

```javascript
$.post("deleteUser",user,res=>{ // user 为 {name:'张三',age:18}
    console.log(res)
})
```

