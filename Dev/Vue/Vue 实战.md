# Vue 实战

## 1. Vue 引言

> `渐进式`  JavaScript 框架

```markdown
# 渐进式
	1. 易用 html css javascript
	2. 高效 开发前端页面
	3. 开发灵活 多样性

# 总结
	Vue 是一个 javascript 框架

# 后端服务端开发人员
	Vue 渐进式 javascript 框架：让我们通过操作很少的 DOM，甚至不需要操作页面中任何 DOM 元素，就能很容易地完成数据和视图绑定 （双向绑定 MVVM）
	
	注意：在使用 Vue 页面中不要再引入jQuery 库
# Vue 作者
	尤雨溪
```



## 2. 入门

### 2.1 下载 Vue.js

```markdown
// 开发版本：
<!-- 开发环境版本，包含了有帮助的命令行警告 -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

//生产版本：
<!-- 生产环境版本，优化了尺寸和速度 -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```



### 2.2 Vue 第一个入门应用

```markdown

<div id="test">{{msg}}
<span id="s">{{pwd}}</span>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app=new Vue({
        el:"#test", // 用来给 Vue 实例定义一个作用范围
        data:{
            msg:'Hello Vue!!',
            pwd:123
        },
    });
</script>

```

```markdown
# 总结：
	1. Vue 实例（对象）中 el 属性：代表 Vue 的作用域，在作用域中都可使用 Vue 的语法
    2. Vue 中 data 属性：用来给 Vue 实例绑定一些相关数据，绑定的数据可以通过 {{变量名}} 在 Vue 作用范围内使用
    3. 在使用 {{}} 进行获取 data 中数据时，可以在 {{}} 中书写表达式
	4. el 属性中可以书写任意的 css 选择器，推荐使用 id 选择器
```



## 3. v-text 和 v-html

### 3.1 v-text

> `v-text`: 用来获取 data 中数据并以文本形式渲染到指定标签内部，类似于 javascrpt 中的 innerText

```markdown
<div id="test">
    <span v-text="msg">asdf</span>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>

    const app = new Vue({
        el: "#test", // 用来给 Vue 实例定义一个作用范围
        data: {
            msg: 'Hello Vue!!',
            user: {
                name: 'rondo',
                pwd: 111
            },
            list:['aaa','bbb','ccc']
        },
    })
    ;
</script>
```

```markdown
# 总结
	1. {{}}（插值表达式）和 v-text 渲染数据的区别：
		a. 使用 v-text 会将标签中原有的数据覆盖，使用 {{}}（插值表达式） 不会覆盖原有数据
		b. 使用 v-text 可以有效避免在网络较慢时使用 {{}} 可能造成的插值闪烁
```

### 3.2 v-html

> `v-html`：用来获取 data 中数据中含有的 html 标签先解析后渲染到指定标签内部，类似于 javascript 中的 innerHTML

## 4. Vue 中的事件绑定 v-on

### 4.1 绑定事件的语法

```markdown
<div id="test">
    <h1 v-text="msg"></h1>
    <h2 v-text="user.age"></h2>
    <button v-on:click="changeAge">增加年龄</button>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app = new Vue({
        el: "#test", // 用来给 Vue 实例定义一个作用范围
        data: { // 用来定义数据
            msg: 'Hello Vue!!',
            user: {
                name: 'rondo'
                ,pwd: 111
                ,age:12
            },
        },
        methods:{ // 用来定义事件
            changeAge:function(){
                alert("事件触发")
            }
        }
    })
</script>
```

```markdown
# 总结
	事件源：事件发生的 dom 元素	事件：发生特定的动作，click 等 监听器：发生特定动作后的处理程序 通常是 js 中的监听函数
	1. 在 vue 中绑定事件是通过 v-on:事件名，如 v-on:click 等
	2. 在 v-on 事件名的赋值语句中是当前时间触发调用的函数名
	3. 在 vue 中事件的函数统一定义在 Vue 实例的 methods 属性中
```

#### 4.2 Vue 事件简化语法

```markdown
<div id="test">
    <h1 v-text="msg"></h1>
    <h2 v-text="user.age"></h2>
    <button v-on:click="changeAge">增加年龄</button>
    <button @click="editAge">通过 @ 绑定事件</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app = new Vue({
        el: "#test", // 用来给 Vue 实例定义一个作用范围
        data: { // 用来定义数据
            msg: 'Hello Vue!!',
            user: {
                name: 'rondo'
                ,pwd: 111
                ,age:12
            },
        },
        methods:{ // 用来定义事件
            changeAge:function(){
                // 获取 data 中的值 this: Vue 实例
                this.user.age++
            },
            editAge(){ // 两种函数写法都行
                // 获取 data 中的值 this: Vue 实例
                this.user.age--
            }
        }
    })
```

```markdown
# 总结
	1. 在 vue 中绑定事件可以通过 @事件名 的形式，如 @click 等
```

### 4.3 事件参数传递

```markdown
<div id="test">
    <h2 v-text="count"></h2>
    <h2 v-text="name"></h2>
    <button @click="changeCount(123,'aaa')">修改为指定值</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app = new Vue({
        el: "#test", // 用来给 Vue 实例定义一个作用范围
        data: { // 用来定义数据
            count:1
            ,name:''

        },
        methods:{ // 用来定义事件
            changeCount(count,name){
                this.count=count;
                this.name=name;
            }
        }
    })
</script>
```

```markdown
# 总结
	1. 在使用事件时，可以直接在事件调用处给事件传递参数，在事件定义处通过定义对应变量接收传递的参数
```

## 5. v-show v-if v-bind

### 5.1 v-show

> `v-show`:用来控制页面元素是否显示，底层通过 display 属性实现

### 5.2 v-if

> `v-if`: 用来控制页面元素是否显示，底层通过对 dom 树节点进行添加或删除实现的

### 5.3 v-bind

> `v-bind`:用来给标签元素绑定相应的属性		*简化写法* **：属性名**  如 `:src`等

## 6.v-for

> `v-for`：遍历对象（数组也是对象）
>
> **`注意：`**在使用 **v-for** 时最好使用 `:key` 并指定一个唯一量，便于 Vue 内部重用和排序 如 `:key="x.id"`

```markdown
<div id="app">
    <span v-for="(user,index) in users" :key="index">
        <span v-text="index+1"></span>
        <span v-text="user.name"></span>
        <span v-text="user.age"></span> <br>
        <span v-for="(v,k,i) in user">
            {{k}} : {{v}} : {{i}} <br>
        </span>
        <br>
    </span>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app = new Vue({
        el: "#app"
        , data: {
            users:[
                {name:'aaa',age:11},
                {name:'bbb',age:22},
                {name:'ccc',age:33},
                {name:'ddd',age:44},
            ]
        }
        , methods: {
        }
    })
</script>
```

```markdown
# 总结
	在使用 v-for 时注意加上 :key 用来给 Vue 内部提供重用和排序的唯一 key
```



## 7.v-model 双向绑定

> `v-model`: 用来绑定标签元素的值与 vue 实例对象中 data 数据保持一致，从而实现双向的数据绑定机制

```html
<div id="app">
    <input type="text" v-model="msg">
    <input type="text" v-model="msg">

    <div v-text="msg"></div>

    <button @click="changeMsg()">修改 msg</button>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app = new Vue({
        el: "#app"
        , data: {
            msg:''
        }
        , methods: {
            changeMsg(msg=123234){
                this.msg=msg;
            }
        }
    })
</script>
```

```markdown
# 总结
	1. 使用 v-model 指定可以实现数据的双向绑定
	2. 所谓双向绑定，表单中数据变化会导致 vue 实例 data 数据变化，反之也是

# MVVM 架构 双向绑定机制
	Model： Vue 实例中绑定的数据
	
	VM： ViewModel 监听器
	
	View： 页面
```

## 8.简单案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>记事本实战</title>

</head>
<body>

<div id="app">
    <label for="">编辑：
        <input type="text" v-model="msg">
    </label>
    <button @click="addTxt">添加记录</button>

    <ul>
        <li v-for="txt,i in txts" :key="i" @mouseenter="chState(i)" @mouseleave="chState(-1)" style="cursor:pointer;">
            <span v-text="txt" style="border-bottom: 1px solid darkgray "></span>
            <button v-show="i==state" @click="del(i)">删除</button>
        </li>
    </ul>

    <div v-text="'共 '+txts.length+ ' 条'"></div>
    <button @click="delAll" v-show="txts.length>0">删除所有</button>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
    const app = new Vue({
        el: "#app"
        , data: {
            msg: '',
            isShowDelBtn: false,
            txts: [],
            state: -1
        }
        , methods: {
            addTxt() {
                if (this.msg != '') {
                    this.txts.push(this.msg)
                    this.msg = ''
                }
            }
            , del(i) {
                this.txts.splice(i, 1)
            }
            , delAll() {
                this.txts = []
            }
            , chState(i) {
                this.state = i;
            }
        }
    })
</script>
</body>
</html>
```

## 9.事件修饰符

### 9.1 stop 事件修饰符

> 用来阻止事件冒泡 如		`@click.stop="btnClick"`

### 9.2 prevent 事件修饰符

> 用来阻止标签默认行为		`@click.prevent="aClick"`

### 9.3 self 事件修饰符

> 用来针对当前标签的事件触发 => 只能触发自己标签上的特定动作事件

9.4 once 事件修饰符

> 用来只执行特定的事件

## 10.按键修饰符

> 用来与键盘中按键事件绑定，用来修饰特定的按键事件的修饰符

```markdown
# 按键修饰符
	.enter		回车
	.tab		TAB 键，捕获 tab 键执行到当前标签时触发
	.delete		退格或删除
	.esc		退出
	.space		空格
	.up			上
	.down		下
	.left		左
	.right		右
```



## 11. Vue 生命周期

### 11.1 Vue 生命周期图示

![img](Vue 实战.assets/lifecycle.png)

```markdown
# Vue 生命周期总结
	1. 初始化阶段
		beforeCreate() { // 1 生命周期中第一个函数，仅仅完成了Vue实例自身事件和生命周期函数的初始化工作, Vue 实例中还没有 el,data,methods 等相关属性
            console.log('1    beforeCreate===================')
            console.log(this.msg);
        }
        , created() { // 2 第二个函数，该函数在执行时 Vue 实例已经初始化了 data 属性和 methods 中相关方法
            console.log('2    created=======================')
            console.log(this.msg);
        }
        , beforeMount() { // 3 第三个函数，该函数在执行时 Vue 将 el 中指定作用范围作为模板编译
            console.log('3    beforeMount=======================')
            console.log(document.getElementById('s').innerText)
        }
        ,mounted(){ // 4 第四个函数，该函数在执行时，已经将数据渲染到界面中并且已经更新页面
            console.log('4    mounted=======================')
            console.log(document.getElementById('s').innerText)
        }
        // ==========================================================
        ,beforeUpdate(){ // 5 第五个函数，该函数是 data 中数据发生变化时调用的，该函数执行时仅仅是 Vue 实例中 data 的数据变化，页面还没有更新
            console.log('5    beforeUpdate=======================')
            console.log(this.msg)
            console.log(document.getElementById('s').innerText)
        },
        updated(){ // 6 第六个函数，该函数执行时 data 中的数据已经发生改变，界面也发生了更新 与 data 中数据一致
            console.log('6    updated=======================')
            console.log(this.msg)
            console.log(document.getElementById('s').innerText)
        }
        // ==========================================================
        ,beforeDestroy(){ // 7 第七个函数， 该函数执行时， Vue 实例中所有数据 都没有销毁
            console.log('7    beforeDestroy=======================')
            console.log(this.msg)
            console.log(document.getElementById('s').innerText)
        }
        ,destroy(){ // 8 第八个函数， 该函数执行时， Vue 实例被销毁
            console.log('8    destroy=======================')
            console.log(this.msg)
            console.log(document.getElementById('s').innerText)
        }
```

