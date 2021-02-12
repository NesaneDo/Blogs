# Axois 封装 get post 请求 Spring Boot 后台接口

Vue 结合 axois 使用，请求 Spring Boot 后台接口

1. Spring Boot 配置

   ```java
   /**
    * 配置类
    */
   @Configuration
   public class InterceptorConfig implements WebMvcConfigurer {
   
       @Autowired
       private SessionInterceptor sessionInterceptor;
       // java.sql.Timestamp 的格式转换器
       @Autowired
       private TimestampConverter timestampConverter;
   
       @Override
       public void addInterceptors(InterceptorRegistry registry) {
           // 如不排除这些类型的文件，则 spring boot 会将所以文件认为是 模板文件 返回，则这些类型的文件无法被正确解析
           registry.addInterceptor(sessionInterceptor).addPathPatterns("/**").excludePathPatterns("/login.html", "/user/login", "/**/*.css", "/**/*.js", "/**/*.png",
                   "/**/*.jpg", "/**/*.jpeg", "/**/*.gif", "/**/fonts/*", "/**/font/*", "/**/*.svg", "/**/*.ico", "/**/*.map", "/**/upload/*");
       }
   
       @Override
       public void addFormatters(FormatterRegistry registry) {
           registry.addConverter(timestampConverter);
       }
   
       @Override
       public void addCorsMappings(CorsRegistry registry) {
   //        registry.addMapping("/**")
   //                .allowedOrigins("*") // 允许所有，一般写允许跨域的域名
   //                .allowCredentials(true)
   //                .allowedHeaders("Access-Control-Allow-Origin:*","Access-Control-Allow-Headers:*")
   //                .allowedMethods("post", "get", "put", "delete","options")
   //                .maxAge(3600);
           registry.addMapping("/**")
                   .allowCredentials(true)
                   .allowedHeaders("*")
                   .allowedOrigins("*")
                   .allowedMethods("*");
       }
   }
   ```

   

2. Vue 配置

   - 新建配置文件 src/config/module.js

     ```javascript
     module.exports = {
         project_name: '项目名',
         host:'localhost', // 服务器
         port:8081, // 端口
         baseUrl: {
             dev: '/api/', // 开发后台接口地址
             pro: '/api/' // 上线后台接口地址
         },
         targetUrl: 'http://xxx.com/api', // 真实目标地址
         rewritedRoot: '/api' // 需要 重写 的，真正请求时会用 targetUrl 代替，起到跨域作用
     }
     ```

   - 新建配置文件 vue.config.js (放到项目目录下，与 package.json 同级)

     ```javascript
     let config=require('./src/config/module.js')
     module.exports= {
         outputDir: 'dist',   // build输出目录
         assetsDir: 'assets', // 静态资源目录（js, css, images）
         lintOnSave: false, // 是否开启eslint
         devServer: {
             open: true, // 是否自动弹出浏览器页面
             host: config.host,
             port: config.port,
             https: false,   // 是否使用https协议
             hotOnly: true, // 是否开启热更新
             proxy: {
                 [config.rewritedRoot]: {
                     target: config.targetUrl, // 真实请求的地址
                     changeOrigin: true,
                     pathRewrite: {
                         [`^${config.rewritedRoot}`]: ''
                     }
                 }
             },
         }
     }
     ```

   

3. 封装 axois get 和 post 请求方法：新建文件 src/api/axios.js

   ```javascript
   import axios from 'axios'
   import qs from 'qs'
   let config=require('@/config/module.js') // @ 代表 src/
   
   /**
    * 接口请求类
    */
   class HttpRequest {
       constructor(baseUrl) {
           this.baseUrl = baseUrl 
           this.queue = {} // 请求队列，暂时用不到
       }
       getDefaultConfig() {
           const config = {
               baseURL: this.baseUrl
               , method: 'get' // 默认 get 请求
               , headers: {
               },
           }
           return config;
       }
       getPostConfig(){
           let options=this.getDefaultConfig()
           options.method='post'
           return options
       }
   
       /**
        * 拦截器
        * @param {axios} instance 
        * @param {string} url 
        */
       interceptors(instance, url) {
           instance.interceptors.request.use(config => {
               // 处理 config
               // console.log(config)
               return config
           })
           instance.interceptors.response.use(res => {
               // 处理结果
               return res.data
           }, err => {
               // console.log(err)
               return err
           })
       }
       /**
        * 配置参数请求方法
        * @param {*} options 
        */
       request(options) {
           const instance = axios.create() // 创建 axios 实例
           options = Object.assign(this.getDefaultConfig(), options) // assign 合并对象
           this.interceptors(instance, options.url)
           return instance(options)
       }
       /**
        * get 方式请求（默认）
        * @param {*} url 接口
        * @param {*} params 参数
        */
       get(url,params={}) {
           const instance = axios.create() // 创建 axios 实例
           let options = this.getDefaultConfig();
           options.url=url
           options.params=params
           // console.log(options);
           this.interceptors(instance, options.url)
           return instance(options)
       }
       /**
        * post 方式请求
        * @param {*} url 接口
        * @param {*} data 数据
        */
       post(url,data={},contentType='application/x-www-form-urlencoded;charset=UTF-8') {
           const instance = axios.create() // 创建 axios 实例
           let options = this.getPostConfig();
           options.url=url
           // options.data=data
           options.data=qs.stringify(data) // 须转化成 query string 方式:key1=value1&key2=value2
           options.headers['Content-Type']=contentType
           console.log(options);
           this.interceptors(instance, options.url)
           return instance(options)
       }
   }
   // 根据项目版本不同（开发或上线）获取根请求地址
   const baseUrl = process.env.NODE_ENV === 'development' ? config.baseUrl.dev : config.baseUrl.pro
   const axiosObj = new HttpRequest(baseUrl)
   export default axiosObj
   ```

   

4. 编写后台接口

   ```java
   /**
    * 测试
    */
   @RequestMapping("api/test")
   @RestController
   public class TestApi extends BaseController {
       /**
        * 测试 get 请求
        * @param account 参数
        * @param password 参数
        * @return json
        */
       @GetMapping("testGet")
       public Map<String,Object> testGet(String account,String password){
           HashMap<String, String> map = new HashMap<>();
           map.put("account",account);
           map.put("password",password);
           return jsonVal("测试 get 请求",1,map,0);
       }
       /**
        * 测试 post 请求
        * @param account 参数
        * @param password 参数
        * @return json
        */
       @PostMapping("testPost")
       public Map<String,Object> testPost(String account,String password){
           HashMap<String, String> map = new HashMap<>();
           map.put("account",account);
           map.put("password",password);
           return jsonVal("测试 post 请求",1,map,0);
       }
   }
   ```

   BaseController 中有一系列的工具方法，如上文中的 jsonVal

   ```java
       /**
        * 数据返回规则
        * @param msg 信息
        * @param code 代码
        * @param obj 数据
        * @param count 数量
        * @return json
        */
       public static Map<String, Object> jsonVal(String msg, int code, Object obj, int count) {
           Map<String, Object> map = new HashMap<>();
           map.put("code", code);
           map.put("msg", msg);
           map.put("data", obj);
           map.put("count", count);
           return map;
       }
   ```

   

5. 编写前台请求方法：新建文件 src/api/test/index.js

   ```javascript
   import axios from '@/api/axios' // 引入自己封装的 axois
   
   const MODULE = 'test/' // 模块名
   
   function url(url) { // 拼接模块名和请求方法
       return MODULE + url
   }
   
   /**
    * 测试 get 请求
    */
   export function testGet(account, password) {
       return axios.get(url('testGet'), { account, password })
   }
   /**
    * 测试 post 请求
    */
   export function testPost(account, password) {
       return axios.post(url('testPost'), { account, password })
   }
   ```

   

6. 测试，新建文件 src/views/Test.vue

   ```javascript
   <template>
       <div>
       <span href="" @click="testGet" class="bg-azure">测试 get 请求</span><br>
       <span href="" @click="testPost" class="bg-azure">测试 post 请求</span>
       </div>
   </template>
   
   <script>
       import * as test from '@/api/test' // 会自动引入 src/api/test/index.js 文件
       export default {
           name: "Profile",
           methods:{
               /**
                * 测试 get 请求
                */
               async testGet(){
                   let res=await test.testGet('get111','password111') // async 与 await 配合使用，让异步方法变同步，因为 axois 是异步请求
                   console.log(res);
               },
   
               async testPost(){
                   let res=await test.testPost('post123','password123')
                   console.log(res);
               }
           }
       }
   </script>
   
   <style lang="less" scoped>
   
   </style>
   ```

   

7. 测试结果

   ```javascript
   // 测试 get 请求
   {
       code: 1
   	count: 0
   	data: {password: "password111", account: "get111"}
   	msg: "测试 get 请求"
   }
   
   // 测试 post 请求
   {
       code: 1
   	count: 0
   	data: {password: "password123", account: "post123"}
   	msg: "测试 post 请求"
   }
   ```

   