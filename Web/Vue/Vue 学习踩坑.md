# Vue 学习踩坑

## 基础

#### Class 与 style 绑定

##### 绑定内联样式

- `v-bind:style` 或 `:style` 设置样式时，官方网站上说 `property ` 名可以用 **小驼峰（camalCase）** 或 **短横线分隔（kebab-case）需要用引号括起来**来命名，如：

  1.

  ```html
  <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
  ```

  2.

  ```html
  <div v-bind:style="{ color: activeColor, 'font-size': fontSize + 'px' }"></div>
  ```

  

  