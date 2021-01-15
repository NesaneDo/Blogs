# Axios

## 1.Axios 基本使用

### 1.1 引言

> `Axios` 是一个异步请求技术，核心作用就是用来在页面中发送异步请求，并获取对应数据在页面中渲染

### 1.2 Axios 第一个程序

​	官方网站：http://axios-js.com/docs/

​	中文网站：http://www.kancloud.cn/yunye/axios/234845

​	安装方式：

- 1 使用 `npm` :

  ```markdown
  npm install axios
  ```

  

- 2 使用 `bower`：(我也不知道啥是 bower)

  ```markdown
  bower install axios
  ```

  

- 使用 `cdn`:

  ```markdown
  <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
  ```

  

#### 1.2.1 GET 方式请求

```javascript
// 发送 get 方式请求
axios.get("http://localhost:9090/axios_test/user/findAll")
.then((res)=>{
    console.log(res)
}).catch((err)=>{
    console.log(err)
})
```

#### 1.2.2 POST 方式请求

```javascript
// 发送 post 方式请求
const user = {username: "rooondo", password: 111111, bir: "2012-12-12", gender: "男"}
axios.post("http://localhost:9090/axios_test/user/save", user)
    .then((res) => {
        console.log(res)
    }).catch((err) => {
    console.log(err)
})
```

#### 1.2.3 axios 并发请求

> `并发请求`: 在同一时刻发送多个请求，并集中处理每个请求的结果

```javascript
function findAll() {
    // 发送 get 方式请求
    return axios.get("http://localhost:9090/axios_test/user/findAll")
}

function save() {
    // 发送 post 方式请求
    const user = {username: "rooondo", password: 111111, bir: "2012-12-12", gender: "男"}
    return axios.post("http://localhost:9090/axios_test/user/save", user)
}

axios.all([findAll(), save()]).then(
    axios.spread((res1, res2) => { // 每个结果对应每个请求
        console.log(res1);
        console.log(res2);
    })
)
```