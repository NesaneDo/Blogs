# Wordpress 插件自定义 CSS

如何在 Wordpress 插件中自定义 CSS：

1. 确认该插件是否支持自定义 CSS：**插件的设置中是否有 Custom CSS（自定义CSS ）选项**

2. 在网页页面中使用 **DevTools**（F12 或者右键检查）

3. 找到需要更改样式的元素并找到一个该插件特有的 **class **或者 **id**

4. 去该插件的设置中找到 **Custom CSS（自定义CSS ）**并修改样式

5. 保存，完成

   ```css
   /* 示例 */
   /* 该插件有个 x-default class，想要添加一个 padding，则： */
   .x-default{
       padding:8px;
   }
   ```

   